# [UnoCSS](https://unocss.nodejs.cn/)

    $ npm add -D unocss

```ts
/* main.js */
import 'virtual:uno.css'
// vite.config.ts
import UnoCSS from 'unocss/vite'
export default defineConfig({ plugins: [UnoCSS()]})
```

**样式重置**

    $ npm add @unocss/reset

```ts

/* main.ts */

// Normalize.css
import '@unocss/reset/normalize.css'

// sanitize.css
import '@unocss/reset/sanitize/sanitize.css'
import '@unocss/reset/sanitize/assets.css'

// Eric Meyer
import '@unocss/reset/eric-meyer.css'

// Tailwind
import '@unocss/reset/tailwind.css'
import '@unocss/reset/tailwind-compat.css'
```

## [配置文件](https://unocss.nodejs.cn/config/) `./uno.config.ts`

```ts
import { defineConfig, presetUno, transformerDirectives } from 'unocss'
export default defineConfig({  
  // 自定义规则
  rules: [],
  // 合并规则 
  shortcuts: { 'btn': 'py-2 px-4' },
  // 应用主题
  theme: { colors: {} },
  // 应用预设  
  presets: [presetUno()],
  // 应用转换器
  transformers: [ transformerDirectives() ],
})
```

## [预设](https://unocss.nodejs.cn/presets/)

**Presets**

| Package                   | Description | 
| ------------------------- | ----------- |
| @unocss/presetUno         | 默认预设 |
| @unocss/presetMini        | 轻量化的 |
| @unocss/presetWind        | 紧凑的, from Tailwind / Windi |
| @unocss/presetAttributify | 属性化模式 |
| @unocss/presetTagify      | 标签化模式 |
| @unocss/presetIcons       | 纯 CSS 图标, from Iconify |
| @unocss/presetWebFonts    | 网络字体, from Google Fonts |
| @unocss/presetTypography  | 排版预设 |
| @unocss/presetRemToPx     | 转换 rem 为 px |

**Transformers 转换器**

| Package                             | Description | 
| ----------------------------------- | ----------- |
| @unocss/transformer-variant-group   | Windi 变体组功能 | 
| @unocss/transformer-directives      | CSS 指令转换, 如 @apply | 
| @unocss/transformer-compile-class   | 将一组类编译为一个类 | 
| @unocss/transformer-attributify-jsx | 支持 JSX/TSX 中的无值属性 | 

**Extractors 提取器**

| Package                              | Description | 
| ------------------------------------ | ----------- |
| @unocss/extractor-pug                | Pug 提取器 |
| @unocss/extractor-svelte             | Svelte 提取器 |
| @unocss/extractor-arbitrary-variants | 提取器支持工具的任意变体 |

## [Tailwind CSS](https://tailwind.nodejs.cn/)

###

**排版**

- text-xs { font-size: 0.75rem; line-height: 1rem; }
- text-sm
- text-base
- text-lg
- `text-[xl ~ 9xl]`
- `text-[size]/[17px]` - 在任何字体大小工具后添加行高
- `text-[14px]` - 指定值
- `hover:text-base` - 伪类
- `md:text-base` - breakpoints

###

**[Icon](https://unocss.nodejs.cn/presets/icons)**

**属性化模式**

以属性形式应用类, 可对类进行分类。

```html
<button
  bg="blue-400 hover:blue-500 dark:blue-500 dark:hover:blue-600"
  text="sm white"
  font="mono light"
  p="y-2 x-4"
  border="2 rounded blue-200"
>
```

**标签化模式**

当只应用单个类时, 可直接作为标签应用。

```html
<text-red> red text </text-red>
<flex> flexbox </flex>
I'm feeling <i-line-md-emoji-grin /> today!
<!-- 带前缀 -->
<un-flex> </un-flex> 
```


