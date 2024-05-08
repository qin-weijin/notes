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