# [FullPage](https://alvarotrigo.com/fullPage/zh/#page1)

## 基本布局

- Section - 竖向滚动页
- Slide - 横向滚动页
- Options - 选项对象

**Install**

    $ npm install --save vue-fullpage.js


```
import 'vue-fullpage.js/dist/style.css'
import './fullpage.scrollHorizontally.min' // Optional. When using fullpage extensions
import VueFullPage from 'vue-fullpage.js'

app.use(VueFullPage)
```


```html
<full-page :options="options" id="fullpage">
  <div class="section"></div>
  <div class="section">
    <div class="slide" data-anchor="slide1"></div>
    <div class="slide" data-anchor="slide2"></div>
  </div>
</full-page>
```

## Options 选项

```js
const options = {
  licenseKey: 'YOUR_KEY_HERE',

  // Navigation
  menu: '#menu',                                        // 自定义导航菜单
  lockAnchors: false,                                   // 确定 URL 中的锚是否在库中完全有效
  anchors:['firstPage', 'secondPage'],                  // 锚点等同 data-anchor 
  navigation: false,                                    // Section 导航锚点
  navigationPosition: 'right',                          // Section 导航锚点定位
  navigationTooltips: ['firstSlide', 'secondSlide'],    // Section 导航锚点提示
  showActiveTooltip: false,                             // 主动显示 navigationTooltips
  slidesNavigation: false,                              // Slide 导航锚点
  slidesNavPosition: 'bottom',                          // Slide 导航锚点定位

  // Scrolling
  css3: true,                                           // 通过 CSS3 or JavaScript 过渡
  scrollingSpeed: 700,                                  // 滚动速度
  autoScrolling: true,                                  // 自动滚动
  fitToSection: true,                                   // 始终填充整个视图
  fitToSectionDelay: 600,
  scrollBar: false,                                     // 启用站点的滚动条
  easing: 'easeInOutCubic',                             // 滚动的过渡效果
  easingcss3: 'ease',                                   // 滚动的过渡效果 CSS3
  loopBottom: false,                                    // 滚动到尽头，返回尾部，垂直的
  loopTop: false,                                       // 滚动到尽头，返回头部，垂直的
  loopHorizontal: true,                                 // 滚动到尽头，返回，垂直的
  continuousVertical: false,                            // 滚动到尽头，继续滚动，水平的
  continuousHorizontal: false,                          // 滚动到尽头，继续滚动，水平的
  scrollHorizontally: false,                            // 鼠标在内部滑动 Section 滚动
  interlockedSlides: false,
  dragAndMove: false,                                   // 禁止鼠标滚动
  offsetSections: false,                                // 提供基于百分比使用非全屏幕 section 的方法
  resetSliders: false,
  fadingEffect: false,
  normalScrollElements: '..normal-scroll-elements',     // 在 Section 内部创建一个滚动空间
  scrollOverflow: true,                                 // 定义在内容大于它的高度的情况下是否为 section/slide 创建滚动
  scrollOverflowMacStyle: false,                        // mac 滚动条
  scrollOverflowReset: false,
  touchSensitivity: 15, // 定义浏览器窗口宽度/高度的百分比，和触发滑动到下一个 section/slide 的距离的灵敏度。
  bigSectionsDestination: 'top | bottom | null',        // 当 Seciton height 大于视图时如何滚动

  // Accessibility
  keyboardScrolling: true,                              // 键盘滚动
  animateAnchor: true,
  recordHistory: true,

  // Design
  controlArrows: true,                                  // Slide 箭头
  controlArrowsHTML: [
    '<div class="fp-arrow"></div>', 
    '<div class="fp-arrow"></div>'
  ],
  verticalCentered: true,                               // 垂直居中
  sectionsColor : ['#ccc', '#fff'],
  paddingTop: '3em',
  paddingBottom: '10px',
  fixedElements: '#header, .footer'                     // 从插件的滚动结构中移除
  responsiveWidth: 0,                                   // 定义断点
  responsiveHeight: 0,                                  // 定义断点
  responsiveSlides: false,                              // 断点触发时 Slide 转变为 Section
  parallax: false,                                      // 使用视差背景效果
  parallaxOptions: {type: 'reveal', percentage: 62, property: 'translate'},
  dropEffect: false,
  dropEffectOptions: { speed: 2300, color: '#F82F4D', zIndex: 9999},
  waterEffect: false,
  waterEffectOptions: { animateContent: true, animateOnMouseMove: true},
  cards: false,
  cardsOptions: {perspective: 100, fadeContent: true, fadeBackground: true},

  // Custom selectors
  sectionSelector: '.section',
  slideSelector: '.slide',

  lazyLoading: true,
  observer: true,
  credits: { enabled: true, label: 'Made with fullPage.js', position: 'right'},

  // Events
  beforeLeave: function(origin, destination, direction, trigger){},
  onLeave: function(origin, destination, direction, trigger){},
  afterLoad: function(origin, destination, direction, trigger){},
  afterRender: function(){},
  afterResize: function(width, height){},
  afterReBuild: function(){},
  afterResponsive: function(isResponsive){},
  afterSlideLoad: function(section, origin, destination, direction, trigger){},
  onSlideLeave: function(section, origin, destination, direction, trigger){},
  onScrollOverflow: function(section, slide, position, direction){}
}
```

## 静态类

| Class                           | Description |
| ------------------------------- | ----------- |
| `.active`                       | Section Slide Menu | 
| `.fp-viewing-[SECTION]-[SLIDE]` | body - 通过类指定锚点 Section Slide |
| `.fp-responsive`                | body - 响应模式 |
| `.fp-enabled`                   | html |
| `.fp-destroyed`                 | fullpage container |
| `.fp-auto-height`               |   |
| `.fp-auto-height-responsive`    |   |
| `.normal-scroll-elements`       | Option normalScrollElements 创建滚动空间 |
