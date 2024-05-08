# [Ant Design](https://ant-design.antgroup.com/index-cn)

  $ npm install antd --save

**图标组件包**

  $ npm install --save @ant-design/icons-vue    

## Theme or ConfigProvider 全局配置设置主题

```tsx
import React from 'react';
import { theme, ConfigProvider } from 'antd';
const { getDesignToken, useToken } = theme;       // Theme API
const globalToken = getDesignToken(config);       // 导出 token
const { token } = useToken();                     // 导出 token
const themeOptions = {
  inherit: Boolean,                               // 继承
  cssVar: Boolean,                                // 开启 CSS 变量
  hashed: Boolean,                                // 生成独立的 hash 值以隔离主题
  // 算法，作为展开梯度变量的公式。
  algorithm: [ theme.defaultAlgorithm, theme.darkAlgorithm, theme.compactAlgorithm ],
  token: AliasToken,                              // 全局样式配置
  components: { [Component]: AliasToken },        // 组件样式配置
}
const App: React.FC = () => (
  <ConfigProvider theme={themeOptions}></ConfigProvider>
)
```

### Token 样式配置

- 基础变量 Seed Token 是捆绑 Theme 的样式。
- 梯度变量 Map Token 是由基础变量派生的具体样式。 `colorPrimaryBg`
- 化名变量 Alias Token 是拥有共性的，用于批处理的特殊梯度变量。`colorLink`