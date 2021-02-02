获取当前账号的基本信息及方案ID。

`MiniAppDesignBaseInfoService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| getDesignBaseInfo() | 获取当前账号信息及方案信息 | - | `baseInfo` |

### 参数

无

### 返回值

#### baseInfo

| 字段 | 说明 | 类型 | 默认值 |
| :-----| :---- | :---- | :----|
| accountName | 设计师昵称 | `string` |  |
| accountPhone | 设计师手机号 | `string` |  |
| userId | 用户ID | `string` |  |
| designId | 方案ID | `string` |  |

### 示例

```js
import { sappSDK } from 'servkit';
import { MiniAppDesignBaseInfoService, MiniAppToastService } from 'custom-miniapp-sdk';

const {
    designBaseInfoService,
    toast,
} = sappSDK.getService({
    designBaseInfoService: MiniAppDesignBaseInfoService,
    toast: MiniAppToastService,
});
if (designBaseInfoService && toast) {
    const baseInfo = await designBaseInfoService.getDesignBaseInfo();
    await toast.info(`方案ID：${baseInfo.designId};帐号ID：${baseInfo.userId};帐号名称: ${baseInfo.accountName}; 帐号手机号：${baseInfo.accountPhone}`);
}
```