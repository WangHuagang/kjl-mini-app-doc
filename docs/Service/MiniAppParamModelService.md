用于获取场景中某个真分类下的模型数量。

`MiniAppParamModelService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| getParamModelCountByCategory() | 获取场景中某个真分类下模型的数量 | `ModelCountOptions` | `number` |
| remove() | 根据模型ID删除指定模型，支持多个同时删除 | `RemoveOptions` | `boolean` |

### 参数

#### ModelCountOptions

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| id | 需要获取的模型的真分类ID | `number[] \| number` | - | 是 |

#### RemoveOptions

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| ids | 需要删除的模型的ID | `number[] \| number` | - | 是 |


### 返回值

无

### 示例

#### 获取真分类为2170的模型数量

``` js
import { sappSDK } from 'servkit';
import { MiniAppParamModelService } from 'custom-miniapp-sdk';

const paramModelService = sappSDK.getService(MiniAppParamModelService);
if (paramModelService) {
    const count = await paramModelService.getParamModelCountByCategory(2170);
    return count;
}
```