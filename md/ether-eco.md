# step1

```shell
create-react-app my-app
```
--
^Note: this is a note

# step2
设置 package.json 如下：

```json
{
  "name": "club-check-in",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "antd-mobile": "^2.2.6",
    "babel-plugin-transform-decorators-legacy": "^1.3.5",
    "mobx": "^5.5.2",
    "mobx-react": "^5.3.6",
    "mobx-react-devtools": "^6.0.3",
    "react": "^16.6.0",
    "react-app-rewire-mobx": "^1.0.9",
    "react-app-rewired": "^1.6.2",
    "react-dom": "^16.6.0",
    "react-router-dom": "^4.3.1",
    "react-scripts": "1.1.4"
  },
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": [
    ">0.2%",
    "not dead",
    "not ie <= 11",
    "not op_mini all"
  ],
  "devDependencies": {
    "babel-plugin-import": "^1.11.0"
  }
}
```
---

`react-scripts`: "1.1.4" 这个必须选择低版本的，才能成功运行，即 yarn start 成功，
但是会有 warnings:

```shell
warning react-scripts > autoprefixer > browserslist@2.11.3: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
warning react-scripts > css-loader > cssnano > autoprefixer > browserslist@1.7.7: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
warning react-scripts > babel-preset-react-app > babel-preset-env > browserslist@2.11.3: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
warning react-scripts > css-loader > cssnano > postcss-merge-rules > browserslist@1.7.7: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
warning react-scripts > css-loader > cssnano > postcss-merge-rules > caniuse-api > browserslist@1.7.7: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
```
 yarn build 失败。
`react-scripts` 的 package.json 如下

```json
"dependencies": {
    "babel-core": "6.26.0",
    "css-loader": "0.28.7",
```
---

报错信息如下：

```shell
$ react-app-rewired build
Creating an optimized production build...
Failed to compile.

./node_modules/antd-mobile/lib/list/style/index.css
Module build failed: BrowserslistError: Unknown browser query `dead`
    at Array.forEach (<anonymous>)


error Command failed with exit code 1.

```
问题所在可能是 css-loader 小于 1.0.0, [问题相关讨论](https://github.com/browserslist/browserslist/issues/266)

---

"react-scripts" >= 2.0.0 的时候, package.json 如下：

```json
"dependencies": {
    "@babel/core": "7.1.0",
    "babel-core": "7.0.0-bridge.0",
    "css-loader": "1.0.0",
```

css loader 符合 1.0.0, 但是 react-app-rewired 需要 react-scripts < 2.0.0，否则报错如下

```shell
./src/index.js
Error: The 'decorators' plugin requires a 'decoratorsBeforeExport' option, whose value must be a boolean. If you are migrating from Babylon/Babel 6 or want to use the old decorators proposal, you should use the 'decorators-legacy' plugin instead of 'decorators'.
```

---

经过寻找各种方法，解决方法是，删除 `package.json` 中 `browserslist` 字段，修改之后的 `package.json` 如下

```json
{
  "name": "club-check-in",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "antd-mobile": "^2.2.6",
    "mobx": "^5.5.2",
    "mobx-react": "^5.3.6",
    "react": "^16.6.0",
    "react-app-rewire-mobx": "^1.0.9",
    "react-app-rewired": "^1.6.2",
    "react-dom": "^16.6.0",
    "react-router-dom": "^4.3.1",
    "react-scripts": "1.1.4",
    "babel-plugin-import": "^1.11.0"
  },
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  }
}
```
---

# step3
需要配置 react-app-rewire-mobx

新建 root/configure-overrides.js

```javascript
const rewireMobX = require("react-app-rewire-mobx");

module.exports = function override(config, env) {
    return rewireMobX(config, env);
};

```
