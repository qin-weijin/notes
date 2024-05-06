# ant design

    $ npm install antd --save

## Theme

```tsx
import { theme, ConfigProvider } from 'antd';
const { getDesignToken, useToken } = theme;       // Theme API
const globalToken = getDesignToken(config);       // 导出 token
const { token } = useToken();                     // 导出 token
const App = () => (
<ConfigProvider theme={{
  inherit: Boolean,                               // 继承
  cssVar: Boolean,                                // 开启 CSS 变量
  hashed: Boolean,                                // 生成独立的 hash 值以隔离主题
  // 基本算法，指定 Seed Token 展开为 Map Token 的公式。
  algorithm: [ theme.defaultAlgorithm, theme.darkAlgorithm, theme.compactAlgorithm ],
  // Components Token
  components: { [Component]: AliasToken },
  token: AliasToken,
}}></ConfigProvider>
)
```

**Seed Token**

基础变量，捆绑主题的一系列样式。

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

**Map Token**

梯度变量，由基础变量派生的具体样式。

- colorPrimaryBg

**Alias Token**

用于批量处理的共性组件样式，特殊处理的梯度变量。

- colorLink

## About 样式兼容

    import { StyleProvider } from '@ant-design/cssinjs';


## Ant Design Vue

    $ cnpm install ant-design-vue@4.x --save

**自动按需引入**

    $ cnpm install unplugin-vue-components -D

vite.config.js

```
import { defineConfig } from 'vite';
import Components from 'unplugin-vue-components/vite';
import { AntDesignVueResolver } from 'unplugin-vue-components/resolvers';
export default defineConfig({
  plugins: [
    // ...
    Components({
      resolvers: [
        AntDesignVueResolver({
          importStyle: false, // css in js
        }),
      ],
    }),
  ],
});    
```
**图标组件包**

    npm install --save @ant-design/icons-vue    