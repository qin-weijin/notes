# [MDN HTML Docs](https://developer.mozilla.org/zh-CN/docs/Web/HTML)

## 语义化标签

| Tag            | Description |
| -------------- | ----------- |
| `<h1 ~ h6>`    | 标题 |
| `<p>`          | 段落 |
| `<article>`    | 章，用于独立的外部内容 |
| `<section>`    | 段，用于内容分段。一般包含标题、描述、内容 |
| `<figure>`     | 独立内容图像、图表、照片、代码，被删除不应该影响正常的文本流。 |
| `<figcaption>` | 独立内容标题 |
| `<header>`     | 页眉 |
| `<footer>`     | 页脚 |
| `<main>`       | 主要内容 |
| `<nav>`        | 导航链接，"可见"或"隐藏"，"内嵌于页面"或"独立的导航栏" |
| `<aside>`      | 定义页面内容之外的内容。 |

## 全局属性

- id 
- class - 类命名应该以功能或内容而非表现形式。
- data-* 
- accesskey 
- autocapitalize 
- autofocus
- contenteditable 
- contextmenu 
- dir 
- draggable
- enterkeyhint
-  exportparts
- hidden 
- inputmode 
- is 
- itemid 
- itemprop 
- itemref
- itemscope 
- itemtype 
- lang
- nonce 
- part
- slot 
- spellcheck 
- style 
- tabIndex - tab 键次序控制
- title
- translate

**更多其他属性**

- `aria-*` - 是一组用于支持残障人士访问的属性。
- `xml: lang`、`xml:base` - XHTML 兼容属性。
- 事件处理程序属性

## Storage API

挂载于 Window.sessionStorage 和 Window.localStorage 属性上，访问该属性返回当前源储存的 Storage 对象。

- sessionStorage - 数据将在页面关闭时销毁。
- localStorage - 数据不会自动销毁，除非通过 Javascript 清除预览器缓存或本地缓存。

**属性和方法**

- `length` 
- `key(index)` - 返回储存的第 n 个健名
- `getItem(key)` - 返回指定健值
- `setItem(key, val)` - 设置或添加指定健值
- `removeItem(key)` - 删除指定健
- `clear()` - 清空所有健

[**StorageEvent API**](https://developer.mozilla.org/zh-CN/docs/Web/API/StorageEvent)

当前页面使用的 storage 被其他页面修改时会触发 StorageEvent 事件。

## HTMML 元素

- `<meta>` - Viewport 标记，用于控制视口大小和形状。

**Video 视频嵌入**

```html
<video
  autoplay='Boolean 自动播放'
  controls='Prop 在视频底部提供控制面板控制音频、暂停等'
  controlslist='nodownload | nofullscreen | noremoteplayback 指示控制面板显示哪些控件'
  crossorigin='anonymous | use-credentials 跨域'
  height=''
  loop='Boolean 循环播放'
  muted='Boolean 静音'
  playsinline='Boolean 内联播放'
  poster='URL 海报'
  preload='none | metadata | auto 预加载设置'
  src=''
  width=''
>

```  
