# [Ant Design](https://ant-design.antgroup.com/index-cn)

  $ npm install antd --save

**图标组件包**

  $ npm install --save @ant-design/icons-vue    

## Theme or ConfigProvider 全局配置设置主题

```tsx
import React from 'react';
import { theme, ConfigProvider } from 'antd';
const { componentDisabled, componentSize } = ConfigProvider.useConfig();  // 获取父 ConfigProvider
const { getDesignToken, useToken } = theme;                               // Theme API
const globalToken = getDesignToken(config);                               // 导出 token
const { token } = useToken();                                             // 导出 token
ConfigProvider.ConfigContext;
ConfigProvider.config({ holderRender: (children) => () });
const themeOptions = {
  inherit: Boolean,                                                       // 继承
  cssVar: Boolean,                                                        // 开启 CSS 变量
  hashed: Boolean,                                                        // 生成独立的 hash 值以隔离主题
  // 算法，作为展开梯度变量的公式。
  algorithm: [ theme.defaultAlgorithm, theme.darkAlgorithm, theme.compactAlgorithm ],
  token: AliasToken,                                                      // 全局样式配置
  components: { [Component]: AliasToken },                                // 组件样式配置
}
const App: React.FC = () => (
  <ConfigProvider theme={themeOptions}></ConfigProvider>
)
```

### Token 样式配置

- 基础变量 Seed Token 是捆绑 Theme 的样式。
- 梯度变量 Map Token 是由基础变量派生的具体样式。 `colorPrimaryBg`
- 化名变量 Alias Token 是拥有共性的，用于批处理的特殊梯度变量。`colorLink`

```tsx
interface AliasToken {
  borderRadius,
  colorBgBase: '#fff',
  colorError,
  colorInfo,
  colorLink,
  colorPrimary: '#1677ff',  // 主题色
  colorSuccess,
  colorTextBase: '#000',    // 文本色
  colorWarning,
  controlHeight,
  fontFamily: '',           // 字体 
  fontFamilyCode: '',       // <Typography> inner family
  fontSize: 14,             // 字号
  LineType,
  lineWidth,
  motion, 关闭内置动效,
  motionBase,
  motionEaseInBack: 'cubic-bezier(0.71, -0.46, 0.88, 0.6)', // 特效曲线
  motionEaseInIOut,
  motionEaseInOutCirc,
  motionEaseInQuint,
  motionEaseOut,
  motionEaseOutBack,
  motionEaseOutCirc,
  motionEaseOutQuint,
  motionUnit,
  opacityImage,
  sizePopupArrow,
  sizeStep,
  sizeUnit,
  wireframe,
  zIndexBase,
  zIndexPopupBase,
}
```

## API

- autoInsertSpaceInButton={true}            // Btn 俩个汉字中间隙
- componentDisabled={false}                 // 禁用状态
- componentSize='small | middle | large'    // 组件尺寸
- csp={ nonce: string }                     // 内容安全策略标头
- direction='ltr | rtl'                     // 方向
- getPopupContainer={()=>document.body}     // Select, Tooltip, Menu 弹出框渲染的父节点
- getTargetContainer={()=>HTMLElement}      // Affix、Anchor 滚动元素容器
- iconPrefixCls='anticon'                   // Icon 前缀
- locale={{}}                               // 语言包配置
- popupMatchSelectWidth={Boolean | Number}  // 下拉菜单和选择器
- popupOverflow='viewport | scroll'         // Select 类组件弹层逻辑
- prefixCls='String'                        // 前缀
- renderEmpty={(componentName)=>ReactNode}  // 自定义组件空状态    
- virtual={true}                            // 虚拟滚动
- warning={ strict: Boolean }               // 警告级别
- wave={wave}                               // 波纹