用于小程序当中，显示或隐藏某一类的商品信息。

`MiniAppModelVisibleService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| showModelByCateId() | 仅显示某一类真分类下的模型信息 | `ModelVisibleOptions` | - |

### 参数

#### ModelVisibleOptions

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| pIds | 需要筛选的模型的真分类ID | `number[] \| number` | - | 是 |
| mode | 0: 仅表示为当前真分类的模型 (默认值) 1: 仅展示为非当前真分类的模型 | `number` | 0 | 否 |
| childAndAssembly | 遍历模型时，是否遍历所有子模型 | `boolean` | false | 否 |

### 返回值

无

### 示例

#### 仅显示真分类为2170的模型

``` js
import { sappSDK } from 'servkit';
import { MiniAppModelVisibleService } from 'custom-miniapp-sdk';

const option = {
  pIds: 2170,
  mode: 0,
  childAndAssembly: true,
};
const modelVisibleService = sappSDK.getService(MiniAppModelVisibleService);
if (modelVisibleService) {
    modelVisibleService.showModelByCateId(option);
}
```