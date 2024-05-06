# Vue Router

```ts
// ./router/index.ts

import { createRouter, createWebHistory } from 'vue-router'
const routes = [ { path: '', name: '', component: () => import('')} ]
const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes,  
})

// ./main.ts

import router from '@/router'
app.use(router)
```

## Vue Router Guards

**全局守卫**
```javascript
createRouterGuards(router: Router) {
  router.beforeEach((to, from) => {
    if (!token) { 
      return false                  - 取消导航
    } else {
      return { name: 'Welcome' }    - 重定向
    }
  });
  // 所有异步守卫确认后，导航确认前触发
  router.beforeResolve(async to => {
    try { 
      await axios.get()
    } catch (error) { return false }
  })
  router.afterEach((to, from, failure) => {});
  router.onError((error) => {});      
}
```
- `to` - 即将要进入的目标。
- `from` - 当前导航正要离开的路由。
- 第三参数 `next()` 已被 `return` 取代。

**特定路由地址守卫**
```javascript
const routes = [
  {
    path: '/users/:id',
    component: UserDetails,
    beforeEnter: (to, from) => {}
  },
]
```
**特定路由组件守卫**

- beforeRouteEnter
- beforeRouteUpdate
- beforeRouteLeave

**START_LOCATION**

表示路由的最初始位置
```javascript
import { START_LOCATION } from 'vue-router'
router.beforeEach((to, from) => {
  if (from === START_LOCATION) {
  } else {}
})
```