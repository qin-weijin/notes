# Vite

    npm create vite [my-project-name] --template [vue]

- vue
- vue-ts
- react
- react-ts    

| package | command |
| ------- | ------- |
| Vuetify    | `$ npm create vuetify` |
| Vue        | `$ npm create vue@latest` |
| vue router | `$ npm install vue-router@4` |
| sass       | `$ npm install -D sass-loader sass` |
| cnpm       | `$ npm install -g cnpm --registry=https://registry.npm.taobao.org` |
| Vite 自动按需引入 | `$ npm install unplugin-vue-components -D` |

## vite.config.ts

创建项目时生成备份 `.vuerc`

```ts
import { resolve } from 'path'
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
// Vite 自动按需引入
import Components from 'unplugin-vue-components/vite';
import { AntDesignVueResolver } from 'unplugin-vue-components/resolvers';
export default defineConfig({
  plugins: [
    vue(),
    Components({
      resolvers: [
        AntDesignVueResolver({  // Vite 自动按需引入
          importStyle: false,   // css in js
        }),
      ],
    }),
  ],
  resolve: {
    alias: { "@": resolve(__dirname, 'src') },
    extensions: ['.js', '.json', '.ts', '.vue']
  }
})
```

