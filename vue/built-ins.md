# 内置属性、指令和组件

## 特殊属性

**ref**

注册 DOM 或子元素引用，将保存到 `this.$refs`。
```
<p ref="pRef"></p>

import { ref } from 'vue'
const pRef = ref()
```

**is**

在外壳组件中，根据不同状态显示不同的真实组件，称为**动态组件**。

	<component :is="vue:my-row-component"><>

**key**

循环渲染中作为子组件的唯一键。

## 动态组件
```html
<KeepAlive>
  <component :is=""></component>
</KeepAlive>
```
**`<KeepAlive>`**

保留动态组件的所有项。`:is`、`v-if`

- `include` - 指定缓存的组件。
- `exclude` - 指定不缓存的组件
- `max` - 指定缓存的最大值。

**`<component>`**

作为动态组件的外壳，不会渲染而是被代替。

## 过渡组件 `<Transition>`

不会渲染 DOM

**Props**

- `name` - String，生成 CSS class 名：`[name]-[transition]`
- `css` - Boolean，是否应用 CSS 过渡类。
- `type` - `transition` | `animation` 过渡类型，区别在过渡何时结束。
- `duration` - Number，定义离开/进入的过渡持续时间。
- `mode` - `out-in`、`in-out`、`default` - 指定"旧元素先过渡 out"、还是"新元素先过渡 in"
- `appear` - 是否初始渲染时过渡
- 指定在过渡的不同阶段应用的类。（进入时、过渡时、离开时）
	+ `enterFromClass`, `enterActiveClass`, `enterToClass`, 
	+ `appearFromClass`, `appearActiveClass`, `appearToClass`, 
	+ `leaveFromClass`, `leaveActiveClass`, `leaveToClass`

**事件**

- `@before-enter`, `@enter`, `@after-enter`, `@enter-cancelled`
- `@appear`, `@after-appear`, `@appear-cancelled`
- `@before-leave`, `@leave`, `@after-leave`, `@leave-cancelled`

**过渡组 `<TransitionGroup>`**

为一组元素指定过渡，它们必须包含独立的 `key` 属性。

- `tag` - String，将 TransitionGroup 渲染为指定标签，默认为不渲染。 
- `moveClass` - String，指定类名，在子节点移动时应用过渡。
- 包含所有 Transition 中的事件和 props

## 内置组件

**传送门 `<Teleport>`**

用于把逻辑上关联但表现上分离的组件部分显示在其他位置。如：点击一个 `<button>` 需要在 `<body>` 显示一个模态框 `</model>`
```html
<button @click="open = true">Open Model<button>
<Teleport to="body">I im Model!</Teleport>
```
- `to` - 传送目标，CSS 选择器、实际元素或 HTMLElement
- `disabled` - Boolean，提供打开和关闭传送的选项。

**`<Suspense>`**

用于等待内部的所有异步组件加载完成时一同显示。

## 插槽

**在子组件中定义插槽**

	<slot name="slotname" :prop="value"></slot>

**在父中应用插槽**

	<template v-slot:slotname="propObj">...<template>

**作用域插槽**

使父组件能够访问插槽内定义的数据，以 props 形式定义的数据都以作用域插槽形式传递给父作用域。

**动态插槽名**

	<template v-slot:[slotname]></template>

## 内置指令

**插值**

- `v-text` - 覆盖文本内容，设置 `Node.textContent`
- `v-html` - 插入 HTML 内容，设置 `Element.innerHTML`

**条件渲染**

- `v-if`、`v-else`、`v-else-if`- 销毁、重构组件
- `v-show` - 设置 `display`

**`v-model` 表单元素双向绑定**

仅 `<input>`、`<select>`、`<textarea>`、`<components>` 可用。

- `.lazy` - 监听 change 事件而非 input
- `.number` - 将输入转换为 `Number`
- `.trim` - 过滤输入俩端空格

**`v-bind` `:` 数据绑定**

- `.camel` - 使用驼峰命名法改变属性。
- `.prop` - 绑定为 DOM property
- `.attr` - 绑定为 DOM attribute

**`v-on` `@` 绑定事件监听器**

- `.stop` - 阻止事件继续传播 `event.stopPropagation()`
- `.prevent`- 阻止事件默认行为 `event.preventDefault()`
- `.capture` - 添加到捕获模式。
- `.self` - 只有事件被绑定该指令的元素触发才执行处理函数。
- `.{keyAlias}` - 指定触发处理函数的按键。
- `.once` - 只触发一次。
- `.left` - 只在点击鼠标左键触发处理函数。
- `.right` - 只在点击鼠标右键触发处理函数。
- `.middle` - 只在点击鼠标中键触发处理函数。
- `.passive` - 附件 DOM 事件。

**其他**

- `v-once` - 渲染一次后固定内容不会再更新，用于优化性能。
- `v-memo` - `any[]`，指定一个数组，若数组内的内容没有发生变化则不会更新，类似 v-once。
- `v-cloak` - 隐藏未完成编译的模板
- `v-pre` - 格式化内容, 类似 `<pre>`，显示原生内容，常用于显示 `{{}}`

**`v-for` 循环渲染**

	<v-for="(item, index) in items" :key="item.id">

**数组操作方法**

	this.items = this.items.filter((item)

直接变更原数组，触发视图更新。

- `push()`
- `pop()`
- `shift()`
- `unshift()`
- `splice()`
- `sort()`
- `reverse()`

不会变更原数组。

- `filter()`
- `concat()`
- `slice()`