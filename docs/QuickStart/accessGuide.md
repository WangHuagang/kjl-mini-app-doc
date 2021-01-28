如果是开发者，需要联系酷家乐的相关人员，开通线上添加本地开发入口的权限。

假定你已经拿到了权限。

## 添加开发入口

打开浏览器开发者工具(F12), 在`console`中，输入如下代码，即添加开发者入口(`url`可以自行更改)。

```js
__addMiniAppEntry('http://localhost:3000')

```
如果需要自定义参数，可以能过如下命令添加：

> [!tip]
> 以下命令须与开发确认，当前访问的是否是最新版本，否则可能不支持改用法；

```js
__addMiniAppEntry({
   url: 'http://localhost:3000',
   appId: 'sapp-dev',
   layout: 'RIGHT_FUNCTION_PANEL'
})
```

> - url:  本地或线上的某个链接 
> - appId： 应用ID，开发中，暂时可以使用sapp-dev（后续更新迭代，可能会失效，请勿在线上环境使用默认sapp-dev）
> - layout:  展示布局，当前支持居中弹层或右侧面板两种展示方式(`DIALOG_CENTER`，`RIGHT_FUNCTION_PANEL`)

---

正确的执行结果如下：

![正确执行结果](//qhstaticssl.kujiale.com/newt/101687/image/png/1611825924947/76A71E3F404E90E19507F40800772CFA.png)

---

如果发现如下报错：

![正确执行结果](//qhstaticssl.kujiale.com/newt/101687/image/png/1611827821785/04C2FC90EE4769F5DE82E456E5A1EDEF.png)

则说明你没有权限，可以联系相关人员，添加权限后，重新刷新页面即可。

!> 如果刷新一次不起作用，可以尝试再次刷新

## 清除开发入口

执行如下代码，可以清除所有入口；

```js
localStorage.removeItem('__CUSTOM__APP_MINI_APP_DEV_ENTRY')
```

## 获取小程序demo代码

见压缩包内的项目源码, [点击下载](//qhstaticssl.kujiale.com/newt/101687/application/xzipcompressed/1611828450629/0C04C5FA4633DB2E15A44BE49958C0BB.zip)

## 运行小程序DEMO

假定，你已经获取到了小程序demo。
打开源码中`README.md`文件，执行相关的命令即可（前提是已经安装了`nodejs`）。命令如下：
---
- 全局安装yarn(项目启动必须使用yarn,暂不支持npm)

`npm install yarn -g`
 
- 进入至项目根目录，执行以下命令，安装依赖安装

`yarn`
 
- 启动项目

`yarn start`

---

启动项目，且已经 `添加了开发入口`后，你可以按如下方式看到对应入口：
1. 进入方案

2. 进入定制（厨卫/全屋）[`图中红框标记位置`]

![进入定制](//qhstaticssl.kujiale.com/newt/101687/image/png/1611828009909/9493E2D577C26534C210E85D8F04FBDD.png)

3. 顶部工具箱(底部dev入口，即刚刚添加的入口)

> [!tip]
> 如果成功执行命令，但仍然看不到入口，可以尝试刷新页面，重复之前步骤；

![工具箱入口](//qhstaticssl.kujiale.com/newt/101687/image/png/1611828072962/A2C0087BCEC280FE5778456B795A6C0C.png)

4. 点击入口，则有如下两种展示效果：

![右侧框](//qhstaticssl.kujiale.com/newt/101687/image/png/1611828135348/9C2588BD6530459A61609F5F77BE31C3.png)

![居中弹框](//qhstaticssl.kujiale.com/newt/101687/image/png/1611828138580/62F24663BC82CFFE8BC549F22E4F2E9A.png)

> 以获取方案信息为例：

![获取方案信息](//qhstaticssl.kujiale.com/newt/101687/image/png/1611828206686/26D2FDCA3D49965D7A08797C6194CB02.png)

示例代码:
```js
// 获取帐号信息
const getUserInfo = async () => {
    const {
        designBaseInfoService,
        toast,
    } = sappSDK.getService({
        designBaseInfoService: MiniAppDesignBaseInfoService,
        toast: MiniAppToastService,
    });
    if (designBaseInfoService && toast) {
        const baseInfo = await designBaseInfoService.getDesignBaseInfo();
        await toast.info(`方案ID：${baseInfo.designId};帐号ID：${baseInfo.userId};帐号名称: ${baseInfo.accountName}; 帐号手机号：${baseInfo.accountPhone}`);
    }
}
```

?> 更多API调用，可以参考DEMO中的代码。

## 添加线上入口

如果需要添加固定入口，可以联系酷家乐相关工作人员。