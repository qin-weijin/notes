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
const App: React.FC = () => (
  <ConfigProvider theme={{
    inherit: Boolean,
    cssVar: Boolean,
    hashed: Boolean,
  }}></ConfigProvider>
)
```

### Token 样式配置

- 基础变量 Seed Token 是捆绑 Theme 的样式。
- 梯度变量 Map Token 是由基础变量派生的具体样式。 `colorPrimaryBg`
- 化名变量 Alias Token 是拥有共性的，用于批处理的特殊梯度变量。`colorLink`