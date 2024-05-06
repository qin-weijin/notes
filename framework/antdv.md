# [Ant Design of Vue](https://www.antdv.com/docs/vue/introduce-cn)

**安装**

    $ npm install ant-design-vue@4.x --save

- 安装和配置自动按需引入, 详见: Vite.md `unplugin-vue-components`

**`./main.ts` 中注册**
```ts
import { createApp } from 'vue';
import App from './App';
// Components
import Antd from 'ant-design-vue';                // 全局引入
import { Button, message } from 'ant-design-vue'; // 局部引入
// Style
import 'ant-design-vue/dist/reset.css';

const app = createApp(App).mount('#app');
app.use(Antd)                                     // 全局注册
app.use(Button).mount('#app');                    // 局部注册 Antd Button
app.config.globalProperties.$message = message;   // 局部挂载 Antd message 到 Vue
```

**`./my-component.vue` 中注册**
```vue
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

## ConfigProvider
```vue
<template>
  <a-config-provider
    :theme="{ 
      inherit: Boolean,  
      token: { colorPrimary: '#00b96b' },                   <!-- Seed | Map | Alias Token -->      
      algorithm: theme.darkAlgorithm,    
      components: { [Radio]: { colorPrimary: '#00b96b', } }
    }"
  ></a-config-provider>
</template>  
<script setup lang='ts'>
  import { theme } from 'ant-design-vue';
  const { 
    useToken, 
    defaultAlgorithm,           // 外部引用主题属性
    defaultSeed 
  } = theme;
  const { token } = useToken(); // 引用当前主题属性
</script>
```

## StyleProvider

```vue
<template>
  <a-style-provider 
    hash-priority="low | high"                            // 开启 :where, 降低 CSS Selector 优先级
    :transformers="[legacyLogicalPropertiesTransformer]"  // 兼容, 转换
    cache={cache}
  ></a-style-provider>
</template>
```

## 高级组件

[Surely Vue](https://www.surely.cool/doc/guide)

解决大数据渲染和图表集成,使用虚拟滚动提升渲染速度，树形数据、展开内容、嵌套子表格、行列合并、自动行高、横向、纵向、吸顶、固定头、固定列等

    npm i --save @surely-vue/table


