# [Ant Design](https://ant-design.antgroup.com/index-cn)

    $ npm install antd --save

**图标组件包**

    $ npm install --save @ant-design/icons-vue    

## Theme or ConfigProvider 全局配置设置主题

```
import { theme, ConfigProvider } from 'antd';
const { getDesignToken, useToken } = theme;       // Theme API
const globalToken = getDesignToken(config);       // 导出 token
const { token } = useToken();                     // 导出 token
const App = () => (
<ConfigProvider theme={{
  inherit: Boolean,                               // 继承
  cssVar: Boolean,                                // 开启 CSS 变量
  hashed: Boolean,                                // 生成独立的 hash 值以隔离主题
  // 算法，作为展开梯度变量的公式。
  algorithm: [ theme.defaultAlgorithm, theme.darkAlgorithm, theme.compactAlgorithm ],
  token: AliasToken,                              // 全局样式配置
  components: { [Component]: AliasToken },        // 组件样式配置
}}></ConfigProvider>
```

### Token 样式配置

- 基础变量 Seed Token 是捆绑 Theme 的样式。
- 梯度变量 Map Token 是由基础变量派生的具体样式。 `colorPrimaryBg`
- 化名变量 Alias Token 是拥有共性的，用于批处理的特殊梯度变量。`colorLink`

```ts
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

## ConfigProvider 全局配置
  
```
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

## [Antd Style](https://ant-design.github.io/antd-style/)

将 CSS 写入 Javascript 的框架。

```
import { createStyles } from 'antd-style';
// css object 写法
const useStyles = createStyles(({ token, css }) => ({
  container: {
    backgroundColor: token.colorBgLayout,
    borderRadius: token.borderRadiusLG,
    maxWidth: 400,
    width: '100%',
    height: 180,
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'column',
    marginLeft: 'auto',
    marginRight: 'auto',
  },
// 字符串写法
  card: css`
    color: ${token.colorTextTertiary};
    box-shadow: ${token.boxShadow};
    &:hover {
      color: ${token.colorTextSecondary};
      box-shadow: ${token.boxShadowSecondary};
    }

    padding: ${token.padding}px;
    border-radius: ${token.borderRadius}px;
    background: ${token.colorBgContainer};
    transition: all 100ms ${token.motionEaseInBack};

    margin-bottom: 8px;
    cursor: pointer;
  `,
}));
export default () => {

  const { styles, cx, theme } = useStyles();

  return (
    // cx 组织 className
    <div className={cx('a-simple-create-style-demo-classname', styles.container)}>
      <div className={styles.card}>createStyles Demo</div>
      {/* theme 对象包含了所有的 token 与主题等信息 */}
      <div>当前主题模式：{theme.appearance}</div>
    </div>
  );
};
```