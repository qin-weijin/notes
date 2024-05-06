# Antd Components

**通用属性**

- `rootClassName` - 组件最外层 className

## Layout Components

```tsx
import { Divider, Flex, Grid, Col, Row, Layout, Space } from 'antd';
const { Header, Footer, Sider, Content } = Layout;
const { useBreakpoint } = Grid;
const screens = useBreakpoint();
const Layout = () => (<>
<Flex     
  vertical                                        // 主轴垂直
  wrap                                            // 单行/多行
  justify                                         // 主轴方向对齐方式
  align                                           // 交叉轴方向对齐方式
  flex                                            // 等同于 CSS Flex
  gap="small | middle | large | string | number"  // 元素间隙
  component="div"                                 // 元素类型 
></Flex>
<Row 
  align="top | middle | bottom | stretch"         // 垂直对齐方式
  align={{[breakpoint]: [value]}}                 // 以对象形式指定特定断点
  gutter={ Number | [x, y] }                      // 间隙 px
  gutter={[breakpoint]: n}                        // 以对象形式指定特定断点
  justify="start | end | center | space-around | space-between | space-evenly" 
  justify={{[breakpoint]: [value]}}               // 水平对齐方式
  wrap                                            // 自动换行
>
  <Col 
    flex="1 1 auto"                               // 等同于 CSS Flex
    offset={Number}                               // 添加左间隔
    order={Number}                                // 顺序
    pull={Number}                                 // 左移
    push={Number}                                 // 右移
    span={Number}                                 // 占位格数
    [breackpoint]={{[key]: [value]}}              // 指定特定断点（xs sm md lg xl xxl）, 支持 Col 所有值
  ></Col>
</Row>
</>)
```

## 导航

```tsx
import { Anchor, Breadcrumb, Dropdown, Menu, Pagination, Steps } from 'antd';

// Menu Item
type ItemType = MenuItemType | SubMenuType | MenuItemGroupType | MenuDividerType;
const items: MenuItem[] = [
  {
    danger: '错误时样式',
    disabled: Boolean,
    icon: <Icon />,
    key: 'key',
    label: '标题',
    title: '收缩时显示的标题'    
  },
  {
    children: ItemType[],  
    disabled: Boolean,
    icon: <Icon />,
    key: 'key',
    label: '标题',
    popupClassName: '子菜单样式',
    popupOffset: [Number, Number],                      // 子菜单偏移量
    onTitleClick: function({ key, domEvent }),          // 点击时
    theme: 'light | dark'
  },
  { type: 'group', label: '', children: MenuItemType[] },
  { type: 'divider', dashed: Boolean },
]

const Navigation = () => (
  <Menu
    defaultOpenKeys={String[]}
    defaultSelectedKeys={String[]}                    // 初始选中的项的键
    expandIcon
    forceSubMenuRender
    inlineCollapsed
    inlineIndent
    items={ItemType[]}                                // 项
    mode='vertical | horizontal | inline'             // 类型垂直、水平、内嵌
    multiple
    openKeys
    overflowedIndicatior
    selectable
    selectedKeys
    style
    subMenuCloseDelay
    subMenuOpenDelay
    theme
    triggerSubMenuAction
    onClick
    onDeselect
    onOpenChange
    onSelect
  ></Menu>
)
```

## Card

```tsx
import { Card } from 'antd';  
const { Meta } = Card;
const Navigation = () => (
  <Card
    actions
  >
    <Card.Grid></Card.Grid>
    <Meta />
  </Card>
)
```

## ConfigProvider 全局配置
  
```tsx
import { Affix, App, ConfigProvider } from 'antd';

const { componentDisabled, componentSize } = ConfigProvider.useConfig(); // 获取父 ConfigProvider

const App: React.FC = () => {
ConfigProvider.ConfigContext
ConfigProvider.config({
  holderRender: (children) => ()
})
return (
  <ConfigProvider
    autoInsertSpaceInButton={true}            // Btn 俩个汉字中间隙
    componentDisabled={false}                 // 禁用状态
    componentSize='small | middle | large'    // 组件尺寸
    csp={ nonce: string }                     // 内容安全策略标头
    direction='ltr | rtl'                     // 方向
    getPopupContainer={()=>document.body}     // Select, Tooltip, Menu 弹出框渲染的父节点
    getTargetContainer={()=>HTMLElement}      // Affix、Anchor 滚动元素容器
    iconPrefixCls='anticon'                   // Icon 前缀
    locale={{}}                               // 语言包配置
    popupMatchSelectWidth={Boolean | Number}  // 下拉菜单和选择器
    popupOverflow='viewport | scroll'         // Select 类组件弹层逻辑
    prefixCls='String'                        // 前缀
    renderEmpty={(componentName)=>ReactNode}  // 自定义组件空状态    
    virtual={true}                            // 虚拟滚动
    warning={ strict: Boolean }               // 警告级别
    wave={wave}                               // 波纹
    theme={{
      token: {},
      components: {}
    }}
  ></ConfigProvider>
)}
```