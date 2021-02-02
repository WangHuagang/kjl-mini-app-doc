小程序启动预置的逻辑，可以设置要启动时要加载的模式，查看当前小程序是否出去open状态，以及关闭当前小程序等等。

`MiniAppBootstrapService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| loadMode() | 加载模式 | `mode` | `void` |
| isOpened() | 是否处于open状态 | - | `boolean` |
| close() | 关闭当前小程序 | - | `void` |

### 参数

#### mode

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| mode | 加载模式 | `number` |  0：内空模式；1：自定义模式； | 是 |

### 返回值

无

### 示例

#### 进入内空模式

``` js
import { sappSDK } from 'servkit';
import { MiniAppBootstrapService } from 'custom-miniapp-sdk';
 
export async function bootstrap() {
  try {
    await sappSDK.setConfig({
      async onShow(sdk) {
        const bootstrapService = await sappSDK.service(MiniAppBootstrapService);
        await bootstrapService.loadMode(0);
      }
    }).start();
  } catch (e){
    console.error(e);
  }
}
```

#### 退出当前小程序
```js
import { sappSDK } from 'servkit';
import { MiniAppBootstrapService } from 'custom-miniapp-sdk';

const onExit = () => {
    const bootstrapService = sappSDK.getService(MiniAppBootstrapService);
    if (bootstrapService) {
        bootstrapService.close();
    }
};
```