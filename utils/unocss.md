# [UnoCSS](https://unocss.nodejs.cn/)

## [集成 Vite](https://unocss.nodejs.cn/integrations/vite)

    $ npm install -D unocss

```ts

// main.ts
  import 'virtual:uno.css'

// vite.config.ts
  import UnoCSS from 'unocss/vite'
  import { defineConfig } from 'vite'
  export default defineConfig({
    plugins: [ UnoCSS() ]
  })
```

## [配置](https://unocss.nodejs.cn/config/)

```ts
// ./uno.config.ts
import { defineConfig } from 'unocss'
export default defineConfig({
  rules: [],                            // 自定义规则
  shortcuts: {},                          // 合并规则
  theme: {},                              // 主题
  variants: [],                           // 变体
  extractors: [],                         // 提取器
  transformers: [],                       // 转换器  
  preflights: [],                         // 初始化
  layers: {},                             // 层
  autocomplete: [],                       // 自动补全
  presets: [presetUno(presetOptions)]     // 预设 - $ npm install -D @unocss/preset-uno
})


/* 预设选项 */

const presetOptions = {
  dark: class,
  attributifyPseudo: false,               // 生成伪选择器
  variablePrefix: 'un-',                  // 自定义属性前缀
  prefix: 'tw-',                          // 添加前缀
  preflight: true                         // CSS Reset  
}
```

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


