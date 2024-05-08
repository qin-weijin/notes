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
		inherit: 'Boolean',
	}}></ConfigProvider>
)
```