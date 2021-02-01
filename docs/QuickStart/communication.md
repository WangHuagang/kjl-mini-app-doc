## 安装SDK

安装由酷家乐提供的`custom-miniapp-sdk`，由于目前还未发布在npm上，可[点击下载](//qhstaticssl.kujiale.com/newt/101687/application/xzipcompressed/1612168464139/5F9123800C9B2AD470E2EFD73302206E.zip)。 下载后解压至项目`node_modules`即可。

## 按需引入

根据需要使用的service从`custom-miniapp-sdk`中按需引入.

> [!warning]
> 未开通对应的service的权限将无法使用，使用之前请联系酷家乐开发人员申请开通权限!

```js
import { MiniAppToastService } from 'custom-miniapp-sdk'; 
```

## 与设计工具通信

此处以`弹框提示信息`为例，演示小程序与设计工具进行数据通信.

### 获取service

通过sappSDK提供的`getService`方法获取对应的service:

```js
import { sappSDK } from 'servkit';
const toast = await sappSDK.getService(MiniAppToastService)
```
`MiniAppToastService`提供了以下几个方法可使用：

- `success`
- `error`
- `info`
- `warn`
- `loading`

### 调用service

获得service后，调用其提供的方法实现与设计工具的通信:

```js
toast.success('success提示信息！');
toast.error('error提示信息！');
toast.info('info提示信息！');
toast.warn('warn提示信息！');
toast.loading('loading提示信息！');
```

## 示例

直接将下面的代码替换`src/App.js`的内容，便实现了小程序使用设计工具提供的弹框信息服务。
```js
import './index.css'
import { sappSDK } from 'servkit';
import { MiniAppToastService } from 'custom-miniapp-sdk';

function App() {

  const toast = (type, message = '') => {
    return async () => {
        const toast = await sappSDK.getService(MiniAppToastService);
        if (!toast) {
            return;
        }
        toast[type](message);
    }
  }

  return (
    <div>
      <h1>小程序启动示例</h1>
      <button onClick={toast('success','这是一条提示信息！！！')}>success提示信息</button>
    </div>
  );
}

export default App;

```

预览效果：

![提示信息预览效果](//qhstaticssl.kujiale.com/newt/101687/image/png/1612170123370/712F351B773D6F487B102E4345E2A20C.png)

?> 更多的SDK service后续章节将会详细介绍！

 {docsify-updated}