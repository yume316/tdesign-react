:: BASE_DOC ::

### 关闭全局提示

#### 带关闭按钮的全局提示

{{ close }}

#### 使用关闭函数控制全局提示

{{ closeFunction }}

#### 关闭多条全局提示

{{ closeAll }}

### 控制全局提示显示位置

{{ offset }}

### 函数式调用

{{ duration }}

## API
### Message Props

名称 | 类型 | 默认值 | 说明 | 必传
-- | -- | -- | -- | --
closeBtn | TNode | undefined | 关闭按钮，可以自定义。值为 true 显示默认关闭按钮，值为 false 不显示关闭按钮。值类型为 string 则直接显示值，如：“关闭”。也可以完全自定义按钮。TS 类型：`string | boolean | TNode`。[通用类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/common.ts) | N
content | TNode | - | 用于自定义消息弹出内容。TS 类型：`string | TNode`。[通用类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/common.ts) | N
duration | Number | 3000 | 消息内置计时器，计时到达时会触发 duration-end 事件。单位：毫秒。值为 0 则表示没有计时器。 | N
icon | TNode | true | 用于自定义消息前面的图标，优先级大于 theme 设定的图标。值为 false 则不显示图标，值为 true 显示 theme 设定图标。TS 类型：`boolean | TNode`。[通用类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/common.ts) | N
theme | String | info | 消息组件风格。可选项：info/success/warning/error/question/loading。TS 类型：`MessageThemeList`。[详细类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/message/type.ts) | N
onCloseBtnClick | Function |  | TS 类型：`(context: { e: MouseEvent }) => void`<br/>当关闭按钮存在时，用户点击关闭按钮触发 | N
onDurationEnd | Function |  | TS 类型：`() => void`<br/>计时结束后触发 | N

### MessageOptions

名称 | 类型 | 默认值 | 说明 | 必传
-- | -- | -- | -- | --
attach | String / Function | 'body' | 指定弹框挂载的父节点。数据类型为 String 时，会被当作选择器处理，进行节点查询。示例：'body' 或 () => document.body。TS 类型：`AttachNode`。[通用类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/common.ts) | N
offset | Array | - | 相对于 placement 的偏移量，示例：[-10, 20] 或 ['10em', '8rem']。TS 类型：`Array<string | number>` | N
placement | String | top | 弹出消息位置。可选项：center/top/left/right/bottom/top-left/top-right/bottom-left/bottom-right。TS 类型：`MessagePlacementList`。[详细类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/message/type.ts) | N
zIndex | Number | 5000 | 消息层级 | N
MessageProps | - | - | 继承 `MessageProps` 中的全部 API | N

### message 或 MessagePlugin

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
theme | String | - | 必需。消息类型。TS 类型：`MessageThemeList`
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>【interface MessageInstance { close: () => void }】`

### message.info 或 MessagePlugin.info

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageInfoOptions`。[详细类型定义](https://github.com/Tencent/tdesign-react/blob/develop/src/message/type.ts)
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.error 或 MessagePlugin.error

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageInfoOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.warning 或 MessagePlugin.warning

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageInfoOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.success 或 MessagePlugin.success

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageInfoOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.loading 或 MessagePlugin.loading

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息提醒内容。TS 类型：`string | MessageInfoOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.question 或 MessagePlugin.question

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
message | String / Object | - | 必需。消息内容。TS 类型：`string | MessageInfoOptions`
duration | Number | 3000 | 消息显示时长，单位：毫秒。值为 0 表示永久显示

插件返回值：`Promise<MessageInstance>`

### message.closeall 或 MessagePlugin.closeAll

这是一个插件函数，参数形式为顺序参数（形如：(a, b, c)），而非对象参数（形如：({ a, b, c })）。顺序参数如下，

参数名称 | 参数类型 | 参数默认值 | 参数说明
-- | -- | -- | --
-- | - | - | --。TS 类型：`--`
