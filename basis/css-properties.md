# CSS Properties 常用属性

## Display 元素类型

```css
.Display {

	display: none; 
	display: contents;                          /* 不产生盒模型，而是被伪盒子和子盒子取代 */

	/* 外部表现 */
	display: block;                             /* 生成块级元素盒，该元素前后在正常流中产生换行 */
	display: inline;                            /* 生成内联元素盒，该元素前后在正常流中不换行 */

	/* 内部表现 */
	display: flow;                              /* 默认，流式布局 */
	display: flow-root;                         /* 块级上下文 */
	display: flex;                              /* 块级 + 弹性盒模型 */
	display: grid;                              /* 块级 + 网络盒模型 */
	display: table;                             /* 块级 + 表格盒模型 */
	display: ruby;                              /* 内联 + ruby 模型 */

	/* CSS2 内外表现连接写法 */
	display: inline-block inline-table inline-flex inline-grid;

	/* 仅 table & ruby 子元素有效 */
	display: list-item;
	display: table-row-group table-header-group table-footer-group;
	display: table-row table-cell table-column table-column-group table-caption;
	display: ruby-base ruby-text ruby-base-container ruby-text-container;
}
```

## Position 定位

```css
.Float {
	float: right left none;           /* 浮动, 可用于设置多列布局, absolute 将忽略浮动 */
	clear: right left none both;      /* 清除浮动, 需添加空元素 */
}
.Position {
	position: static;                 /* 无法调整位置 */
	position: relative;               /* 相对定位，保留原位再调整位置 */
	position: absolute;               /* 绝对定位，不保留原位，根据最近非 static 元素调整位置 */
	position: fixed;                  /* 绝对定位，不保留原位，根据视口调整位置 */
	position: sticky;                 /* 粘性定位，根据最近滚动元素定位吸顶。滚动到达临界点时从 absolute 变为 fixed */

	top: auto;
	right: auto;
	bottom: auto;                     /* 元素底边缘与父底边缘距离 */
	left: auto;

	z-index: ;
}
```

## Box 盒模型

```css
.Box-Model {
	width: ;                          /* min- max- */
	height: ;
	margin: ;
	padding: ;
	border: 1px solid red;            /* 边框 -bottom -left -right -top */
	border-color: ;
	border-style: ;
	border-width: ;
	border-radius: ;
	border-image: ;                   /* -outset -repeat -slice -source -width */
	outline: 1px solid red;           /* 轮廓: size style color */
	box-shadow: 5px 5px 5px 5px red;  /* 阴影: x y distance size color inset outset */
}
/* 对齐 */
.Alignment {
	/* 行内轴  */
	justify-items: ;
	justify-self: ;
	justify-content: ;
	/*块轴*/
	align-items: ;
	align-self: ;
	align-content: ;
}
```

## Font & Text 文本和字体

```css
.Font {
	font: ;                                                           /* shorthand */
	font-family: ;
	font-size: 1rem;
	font-weight: 700;
	font-style: normal italic oblique;                                /* 正常、斜体、倾斜 */
	font-variant: ; /* shorthand, -alternates -caps -east-asian -emoji -ligatures -numeric -position -settings */
	font-size-adjust: ;                                               /* 尺寸 */
	font-stretch: ;                                                   /* 紧缩或伸展 */

};
@font-face { font-family: quote; src: local(); unicode-range: ; }   /* 指定字体的引用地址 */
.Text {
	color: red;                                                       /* 颜色 */
	line-height: normal;                                              /* 行高 */
	word-spacing: normal;                                             /* 字间距 */   
	text-align: left right center justify;                            /* 文本对齐方式 */
	vertical-align: baseline top bottom text-top middle text-bottom;  /* 指定内联元素基线 */
	vertical-align: sub super [number] [n%];                          /* 文本上下标、继承、数字、百分比 */
	text-decoration: none underline overline line-through blink;      /* 文本修饰，如去除 <a> 下划线 */
	word-wrap: normal;                                                /* 换行方式 */
	text-overflow: clip ellipsis [string];                            /* 文本溢出 */
	text-indent: ;                                                    /* 首行缩进 */  
	text-shadow: ;                                                    /* 文本阴影 */
	text-transform: none uppercase lowercase capitalize;              /* 大小写转换 */
	white-space: ;
	letter-spacing: ;                                                 /* 字符间距 */  
}
```

## Table & List 表单和列表

```css
.Table {
	border-spacing: ;                                                 /* 单元格距离 */
	caption-side: ;                                                   /* 标题位置 */
	empty-cells: ;                                                    /* 是否显示空单元格 */
	table-layout: ;                                                   /* 算法 */
};
.List {
	list-style-position: none disc circle square;                     /* 项前图标: 去除、实心圆、空心圆、实心方块 */
	list-style-image: url();                                          /* 项前图像 */
	column-count: auto;                                               /* 列布局 */
	column-gap: 1px;                                                  /* 列距离 */
	column-rule: red;                                                 /* 列宽度 样式 颜色 */ 
}
```

## Transition 过渡

```css
.Transition {
	transition: ;
	transition-delay: ;                  /* 开始时间 */
	transition-property: ;               /* 过渡的属性 */
	transition-duration: ;               /* 持续周期 */
	transition-timing-function: "ease";  /* 时间曲线 */


}
```

## Transition 特效

```css
.Animation {
	animation: ;
	animation-delay: ;                   /* 开始时间 */
	animation-direction: ;               /* 逆向播放 */
	animation-duration: ;                /* 持续周期 */
	animation-fill-mode: ;               /* 动画之外的状态 */
	animation-iteration-count: ;         /* 循环次数 */
	animation-name: ;                    /* 关键帧名 */
	animation-play-state: ;              /* 运行或暂停 */
	animation-timing-function: ;         /* 时间曲线 */
}
/* 定义关键帧 */
@keyframes keyframesName {
	n { attr:"value" }
	from {}
	to {}
}
```

## Transform 变形

	transform: Function

```
matrix(n,n,n,n,n,n)                    /* 转换，使用六个值的矩阵 */
translate(x,y)                         /* 转换，沿着 X 和 Y 轴移动元素 */
translateX(n)                          /* 转换，沿着 X 轴移动元素 */
translateY(n)                          /* 转换，沿着 Y 轴移动元素 */
scale(x,y)                             /* 缩放，改变元素的宽度和高度 */ 
scaleX(n)                              /* 缩放，改变元素的宽度 */
scaleY(n)                              /* 缩放，改变元素的高度 */ 
rotate(angle)                          /* 旋转，在参数中规定角度 */
rotateX()             
rotateY()             
skew(x-angle,y-angle)                  /* 倾斜，沿着 X 和 Y 轴 */
skewX(angle)                           /* 倾斜，沿着 X 轴 */
skewY(angle)                           /* 倾斜，沿着 Y 轴 */
```

## More 更多

```css
.More {
	opacity: ;                                                        /* 不透明度 */ 
	overflow: visible hidden clip scroll auto hidden visible;         /* 溢出 -x -y -wrap */
	visibility: hidden visible;                                       /* 可见性，占据文本流空间 */
	z-index: ;
	clip: ;                                                           /* 形状 */
	cursor: auto default none;                                        /* 光标类型 */
	cursor: pointer text grab all-scroll zoom-in zoom-out;  
}
.Background {
	background-color: rgb(0, 0, 0); 
	background-image: url();
	background-size: ;
	background-repeat: repeat repeat-x repeat-y no-repeat;            /* 平铺方式 */
	background-position: top right bottom left;                       /* 背景定位 -x -y */
	background-attachment: scroll fixed;                              /* 背景固定或随页面滚动 */
	background-origin: content-box padding-box border-box;            /* 背景图原点 */
	background-clip: content-box padding-box content-box;             /* 背景修剪形状 */  
}
```
