## 安装

####  使用 npm 或 yarn 安装

``` 
$ npm install servkit

```

``` 
$ yarn add servkit

```

如果你的网络环境不佳，推荐使用 [cnpm](https://github.com/cnpm/cnpm)。

#### 按需引用

```js
import { sappSDK } from 'servkit';
```

## 启动

通过调用`start()`方法启动小程序。

> [!tip]
> 页面启动需要在sapp启动之后。

```js
import { sappSDK } from 'servkit';

sappSDK.start();
```
在启动的时候可以通过`setConfig({})`设置相关配置，后续的文档将会详细介绍。

## 示例

这里以使用react脚手架`create-react-app`快速搭建项目为例，目录结构如下(已删除没啥用的文件)：

<pre>
├─ src
│  ├─ App.css // App组件样式文件
│  ├─ App.js // App组件
│  ├─ core
│  │  └─ index.js // 启动sapp
│  ├─ index.js // 入口文件
│  ├─ main.js // 启动应用
</pre>

### 启动sapp

在项目`src`目录下新建`core/index.js`：

```js
import { sappSDK } from 'servkit';
 
export async function bootstrap() {
  try {
    await sappSDK.start();
  } catch (e) {
    throw err('start up sapp fail!');
  }
}

```
### 启动应用

在项目`src`目录下新建`main.js`：

```js
import React from 'react';
import ReactDom from 'react-dom';
import App from './App';

export function bootstrap() {
  ReactDom.render(<App />, document.querySelector('#root'));
}
```

### 修改App组件

修改`src/App.js`:
```js
import './App.css'

function App() {
  return (
    <div>
      <h1>小程序启动示例</h1>
    </div>
  );
}

export default App;

```

### 修改入口

修改入口文件`src/index.js`：
```js
import { bootstrap } from './core';
import { bootstrap as viewBootstrap } from './main';

bootstrap().then(() => {
  viewBootstrap();
});
```

## 调试

只需要在酷家乐设计工具中添加入口即可本地调试小程序代码，如何添加入口可参见 [小程序接入指南.](/QuickStart/accessGuide.md)

## 预览

点击添加后的入口，即可看见本地小程序在酷家乐设计工具中打开, 如下图：

![小程序启动示例](//qhstaticssl.kujiale.com/newt/101687/image/png/1612162676461/1E2A63269C313B7FE5A4BE7B2346BC48.png)

 {docsify-updated}

