# CSS 层叠样式表

## About Centering 元素居中

```css
/* absolute 绝对定位居中 */
.container { position: relative }
.child { 
  position: absolute; 
  top: 50%; 
  left: 50%;
  transform: translate(-50%, -50%);
}

/* 块容器内容居中 */
.container { 
  display: block;
  text-align: center;
  padding-top: 50px;
  padding-bottom: 50px;
  height: 200px; 
  line-height: 200px; 
} 
/* 块元素 */
.block { display: block; margin: auto; }
/* 行内元素, 对齐其他元素 */
.inline { display: inline; vertical-align: middle; }

/* 弹性容器内容居中 */
.flexbox { 
  display: flex;
  align-items: center;
  justify-content: center; 
}
```

## About Organization 模块化

**OOCSS** 

将样式分解成可复用的对象。

```html
<div class="media">
	<li class="list-item"><div class="content"></div></li>	
</div>
```
```css
.media {}
.media .content {}
.list-item {}
.list-item .content{}
```

**BEM**

- B - 将单个组件看作独立的样式块。
- E - 元素作为块的组成部分，使用 `__` 连接。
- M - 修饰符描述元素状态，使用 `--` 连接。

```html
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input class="form__submit form__submit--disabled" type="submit" />
</form>
```

## About Optimize 性能优化

**高消耗属性**

- box-shadows
- border-radius
- transparency
- transforms
- filters
- Float

**动画优化**

- JavaScript 动画尽量使用 requestAnimationFrame，避免 setTimeout, setInterval。
- 尽量使用 CSS 声明动画
- 使用 absolute 取代 translate 

**选择器优化**

- 预览器会从右到左遍历 CSS 选择器给定范围
- 最右端 CSS 选择器为"关键选择器"
- 避免使用通用选择器
- 避免使用多层标签选择器

```css
/* 避免使用标签限制 Class */
treecell.indented {…}               /* Not */
.treecell-indented {…}              /* Recommended */
/* 避免使用子选择器*/
treehead treerow treecell {…}       /* Not */
treehead > treerow > treecell {…}   /* Recommended */
/* 使用继承减少子选择器 */
#bookmarkMenuItem > .menu-left { list-style-image: url(blah) } /* Not */
#bookmarkMenuItem { list-style-image: url(blah) }              /* Recommended */
```

## More

**浏览器前缀**

- `-webkit-` safari、chrome
- `-ms-` IE
- `-moz-` firefox

**CSS Sprite**

雪碧图，将图标压缩到一张图片，通过 background-position 定位应用图标。