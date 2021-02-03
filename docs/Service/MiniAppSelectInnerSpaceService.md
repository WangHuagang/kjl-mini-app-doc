获取当前选中模型的内空尺寸。

`MiniAppSelectInnerSpaceService`提供了一些静态方法，使用方式和参数如下：

### 方法


| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| getSelectedInnerSpace() | 获取当前选中内空尺寸及当前内空的相对坐标 | - | `InnerSpaceResult` |
| unSelected() | 取消选中当前模型 | - | `boolean` |
| watcher | 监听选中模型的数据 | - | `InnerSpaceResult` |

### 参数

无

### 返回值

#### InnerSpaceResult

| 字段 | 说明 | 类型 | 示例 |
| :-----| :---- | :---- | :----|
| parentModelId | 当前选中模型的ID | `string` | `3F2312213` |
| width | 模型宽度 | `number` | `200` |
| height | 模型高度 | `number` | `52` |
| depth | 模型深度 | `number` | `125` |
| position | 当前选中内空的相对坐标 | `Number3` | `{x: 20, y: 30, z: 100} `|

### 示例

#### 获取选中模型数据

``` js
import { sappSDK } from 'servkit';
import { MiniAppSelectInnerSpaceService } from 'custom-miniapp-sdk';
 
const getSelectedModel = async () => {
  const selectModelService = sappSDK.getService(MiniAppSelectInnerSpaceService);
  if (selectModelService) {
      const model = await selectModelService.getSelectedInnerSpace();
      return model;
  }
}
```

#### 取消选中模型
```js
import { sappSDK } from 'servkit';
import { MiniAppSelectInnerSpaceService } from 'custom-miniapp-sdk';

const unSelectedModel = () => {
  const unSelectModelService = sappSDK.getService(MiniAppSelectInnerSpaceService);
  if (unSelectModelService) {
    unSelectModelService.unSelected();
  }
}
```

#### 监听选中模型
```js
import { sappSDK } from 'servkit';
import { MiniAppSelectInnerSpaceService } from 'custom-miniapp-sdk';

const unSelectedModel = () => {
  const selectModelService = sappSDK.getService(MiniAppSelectInnerSpaceService);
  if (selectModelService) {
    selectModelService.watcher.on((model) => {
      console.log(model);
    });
  }
}
```