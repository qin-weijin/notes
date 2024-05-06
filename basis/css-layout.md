# CSS Layout

## Flex Layout

通过 `display: flex | inline-flex` 定义的元素称为 flexbox

**Flexbox**

Flexbox 盒容器中的直系子元素都作为 flex 元素。

```css
.flex-box {
	flex-flow: [flex-direction] [flex-wrap];
	flex-direction: row row-reverse column column-reverse;                            /* 主轴方向 */
	flex-wrap: nowrap wrap wrap-reverse  ;                                       	    /* 换行方式 */
	justify-content: flex-start flex-end center space-between space-around;           /* 水平对齐方式 */
	align-items: flex-start flex-end center baseline stretch;                         /* 垂直对齐方式 */
	align-content: flex-start flex-end center space-between |space-around stretch;    /* 多行对齐方式 */
}
```

**Flex**

```css
.flex {
	flex: [flex-grow] [flex-shrink] [flex-basis];
	flex-grow: number;                                  /* 多余空间放大份额 */
	flex-shrink: number;                              	/* 不足空间缩小份额 */
	flex-basis: auto;                                 	/* 缩放基准值，auto: 以元素宽高为基准 */
	order: number;                                      /* 排序 */
	align-self: auto stretch center flex-start flex-end baseline;	/* 副轴对齐方式 */
}
.flex {
	flex: initial;                                     /* 只允许缩小，等同于 flex: 0 1 auto */
	flex: auto;                                        /* 允许缩放，等同于 flex: 1 1 auto */
	flex: none;                                        /* 禁止缩放，等同于 flex: 0 0 auto */
	flex: number;                                    	 /* 禁止缩小，指定放大倍数，等同于 flex: Number 0 auto */
}
```

**计算 Flex 元素尺寸**

	Flex 元素实际尺寸 = 基准值 + (剩余空间 * 缩放值)
	
	缩放值 = 放大/缩小份额 ÷ 放大/缩写总份额

