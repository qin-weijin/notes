# 单文件组件

单文件组件(即 `*.vue` 文件 Single-File Component，简称 SFC) 使我们能够将 Vue 组件的模板、逻辑和样式封装在单个文件中。
SFC 可通过文件名引用自身，还可通过 `<Form.Input>` 形式引用内部组件。

**单文件组件中的 API 使用**
```javascript
import {defineProps, defineEmits, useAttrs, useSlots, defineExpose, provide, inject} from 'vue'

const props = defineProps({ name: "VApp" })
const emits = defineEmits(['change', 'delete'])
const attrs = useAttrs()
const slots = useSlots()

defineExpose({a, b})	// 显式地指定（暴露）能被父组件访问的属性和函数
provide(key, value)
inject(key, defaultValue, treatDefaultAsctory)
```
**SFC 语言块**

| Module                  | Description |
| ----------------------- | ----------- |
| `<template>` 						| 组件模板, 预编译为 `render` 渲染函数。 |
| `<script setup>` 				| 预编译为 `setup()` 函数，每次组件实例被创建时执行。 |
| `<script>` 							| 区别于 `<script setup>` 它只在组件首次引入时候执行。 |
| `<script lang="ts">` 		| 指定预处理器。 | 
| `<script src="./mod">` 	| 导入模块。 | 
| `<style scoped>` 				| 作用域样式, 在模板和样式命名中添加哈希码命名的私有属性, 使样式只对当前组件生效。 |
| `<style module="mod">` 	| 将被编译为模块并暴露 `$style` 对象 |

**只能使用 `<script>` 的场景**

- `inheritAttrs` 禁止透传无法在 setup 中声明。
- 创建只需要执行一次的对象。
- 声明命名导出。

**样式模块引用**

样式模块通过 `mod.[class]` 或 `useCssModule('mod')` 引用。

```
<div class="$style.header"></div>
<style module="mod">
  .header {
    color: red,
    background: yellow
  }
<style>
```

**样式选择器**

| 深度选择器 | `.a :deep(.b) {}`  | 作用域样式渗透，编译为：`.a[data-v-f3f3eg9] .b {}` | 
| 插槽选择器 | `:slotted(div) {}` | `<slot>` 内容需要通过插槽选择器伪类指定才会生效。 |
| 全局选择器 | `:global(.red) {}` | 将样式应用到全局 |

**CSS 中的 `v-bind()`**

在 CSS 中使用 `v-bind()` 将数据和样式绑定在一起，使样式可试实时响应数据变化。

```
<script setup>
  const theme = { 
    color: "red",
    width: "200px", 
  }
<script>
<style lang="sass" scoped>
  .text
    color: v-bind('theme.color')
</style>
```