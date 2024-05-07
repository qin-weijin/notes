# [Antdv](https://www.antdv.com/docs/vue/introduce-cn)

    $ npm install ant-design-vue@4.x --save

**全局注册**

`main.ts`

```tsx
import Antd from 'ant-design-vue';                // 全局引入
import { Button, message } from 'ant-design-vue'; // 局部引入
import 'ant-design-vue/dist/reset.css';           // Style
const app = createApp(App).mount('#app');
app.use(Antd)                                     // 全局注册
app.use(Button).mount('#app');                    // 局部注册 Antd Button
app.config.globalProperties.$message = message;   // 局部挂载 Antd message 到 Vue
```

**组件中注册**

```
<template>
  <a-button>Add</a-button>
</template>
<script>
  import { Button } from 'ant-design-vue';
  const ButtonGroup = Button.Group;
  export default {
    components: {
      AButton: Button,
      AButtonGroup: ButtonGroup,
    },
  };
</script>
```

## ConfigProvider 全局配置

**配置主题**

```
<a-config-provider
  :theme="{ 
    inherit: Boolean,    
    token: { colorPrimary: '#00b96b' },     <!-- Seed | Map | Alias Token -->
    algorithm: theme.darkAlgorithm | theme.defaultAlgorithm,
    components: { [Radio]: { colorPrimary: '#00b96b', } }
  }"
>
```

**主题实例**

```
import { theme } from 'ant-design-vue'
const { useToken, defaultSeed } = theme;
const { token } = useToken();             // 应用当前属性如: token.colorPrimary
```

## App 包裹组件

- 提供静态方法 `message.xxx`、`Modal.xxx`、`notification.xxx`
- 提供 CSS Reset

```
<a-app></a-app>

const { 
  message, 
  modal, 
  notification 
} = App.useApp()

const showMessage = () => { message.success('Success!') }
```