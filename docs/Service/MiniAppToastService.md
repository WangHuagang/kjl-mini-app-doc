
全局展示操作反馈信息。

`MiniAppToastService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| success() | 成功提示信息 | `option` | - |
| error() | 错误提示信息 | `option` | - |
| info() | 普通提示信息 | `option` | - |
| warn() | 警告提示信息 | `option` | - |
| loading() | 加载提示信息 | `option` | - |

### 参数

#### option

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| timeout | 展示的时间 | `number` | 3000（ms） | 否 |
| content | 展示的内容 | `string` | - | 是 |

### 示例

```js
import { sappSDK } from 'servkit';
import { MiniAppToastService } from 'custom-miniapp-sdk';

const toast = await sappSDK.getService(MiniAppToastService)

toast.success('success提示信息！');
toast.error('error提示信息！');
toast.info('info提示信息！');
toast.warn('warn提示信息！');
toast.loading({timeout: 5000, content: '5秒后会消失的提示框!'});
```