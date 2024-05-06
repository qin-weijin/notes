## 将 Vue 项目部署到 GitHub Pages

- 将 Vite + Vue 项目部署到 `https://<USERNAME>.github.io/<REPO>/`
- 构建代码储存到 gh-pages 分支。`$ npm run build`
- 项目源码储存到 main 分支。
- 修改路由入口使其匹配仓库。 `path: '/<REPO>'`

**修改项目入口 `vite.config.ts`**
```ts
export default defineConfig({
  base: "/<REPO>/",
})
```
**修改路由入口 `./router/index.ts`**
``` ts
import { createRouter, createWebHistory } from 'vue-router'
const routes = [
  {
    path: '/<REPO>',
    component: () => import('@/../index.vue'),
  },
]
const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes,
})
```

**配置上传忽略文件 `.gitignore`**
```
node_modules
dist
...
```
**安装构建工具**

    $ npm install gh-pages --save-dev

**配置到命令行 `packjson.json`**
```json
{
  "scripts": {
    "deploy": "gh-pages -d dist -r https://github.com/<USERNAME>/<REPO>.git -b gh-pages"    
  }
}
```
**运行命令上传项目**

    $ npm run build
    $ npm run deploy

