获取选中模型数据以及设置需要选中的模型。

`MiniAppSelectModelService`提供了一些静态方法，使用方式和参数如下：

### 方法

| 方法 | 描述 | 参数 | 返回值 |
| :-----| :---- | :---- | :---- |
| getSelected() | 获取当前选中的模型数据 | `getSelectedOption` | `getSelectedResult` |
| unSelected() | 取消选中当前模型 | - | `boolean` |
| watcher | 监听选中模型的数据 | - | `getSelectedResult` |
| select | 设置选中内容 | `selectOption` | `boolean` |
| setSelectAbleByCategories | 设置某些真分类模型才可以被选中 | `setSelectAbleByCategoriesOption` | `boolean` |
| setSelectedByCategories | 选中某一真分类下的模型 | `setSelectAbleByCategoriesOption` | `boolean` |

### 参数

#### getSelectedOption

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| full | 是否需要获取更完整的数据信息 | `boolean` | false | 否 |

#### selectOption

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| id | 需要选中的模型ID | `string \| number \| Array<string \| number>` | - | 是 |

#### setSelectAbleByCategoriesOption

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| categorieIds | 能够被选中的模型的真分类ID | `number[] \| number` | - | 是 |

#### setSelectAbleByCategoriesOption

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| :-----| :---- | :---- | :----| :---- |
| categorieIds | 需要选中的模型的真分类ID | `number[] \| number` | - | 是 |

### 返回值

#### getSelectedResult

| 字段 | 说明 | 类型 | 示例 |
| :-----| :---- | :---- | :----|
| id | 模型的ID | `string` |
| position | 当前ParamModel所处的位置 | `Number3` | 
| rotate | 旋转 | `Number3` | 
| size | 尺寸 | `Number3` |
| scale | 缩放 | `Number3` | 
| translation | 偏移 | `Number3` | 
| brandGoodId | ParamModel的商品ID | `number` | 
| params | 子模型当中，可以读取到的参数信息 | `ParamData[]` | 
| name | 模型名称 | `string` |
| children | 包含的子模型 | `IParamModelLiteData[]` |
| accessories | 包含的assesory | `IParamModelLiteData[]` |
| matrix4 | 矩阵 | `string` |
| categories | 所处分类集合 | `number[] \| string[]` |
| materialBrandGoodId | 材质ID | `number` |
| isRoot | 是否是顶层模型 | `boolean` |
| root | 模型数据 | `IParamModelLiteData` |

### 示例
