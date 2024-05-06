# Vue Router

路由使页面无需重新加载即可更改 URL

**createRouter 创建路由实例**

	const VueRouter = createRouter(RouterOptions): Router

**useRouter 返回路由器实例**

	const router = useRouter(): Router

**useRoute 返回当前路由地址**	

	const route = useRoute(): RouteLocationNormalizedLoaded

**useLink 暴露路由链接方法**
```javascript
const {
  route,                    - 解析的路由对象
  herf,                     - 链接中的 ref
  isActive,                 - 当前链接是否被匹配
  isExactActive,            - 当前链接是否被严格匹配
  navigate,                 - 导航到该链接的函数
} = useLink()
```
v-slot 可访问所有 useLink 返回的值。

	<router-link v-slot='{ useLink }'>

## Interfaces Router 路由实例

**Properties**

- `currentRoute` - RouteLocationNormalized，只读，当前路由地址。
- `listening` - 关闭历史事件监听器。
- `options` - RouterOptions

**Methods**

- `addRoute(parentName, route)` - 添加或覆盖一条路由记录。
- `getRoutes()` - 获取所有 路由记录的完整列表
- `go(n)` - 从当前跳转到 n 指定的历史记录位置。
- `back()` - 等同于 `router.go(-1)`
- `forward()` - 等同于 `router.go(1)`
- `hasRoute(name)` - 检测是否存在指定路由器
- `isReady()` - 完成初始化时调用，包括异步组件和异步钩子。
- `onError(callback)` - 路由错误时调用
- `push(location, onComplete?, onAbort?)` - 跳转到 to 指定位置，添加历史记录。
- `removeRoute(name)` - 删除指定名称路由。
- `replace(location, onComplete?, onAbort?)` - 跳转到 to 指定位置，不添加历史记录。
- `resolve(location, current?, append?)` - 解析当前位置
- `afterEach((to, from, failure) => {})` - 添加导航守卫
- `beforeEach((to, from, next) => {})	` - 添加导航守卫			
- `beforeResolve((to, from, next) => {})` - 添加导航守卫

## Interfaces

**RouterViewProps 路由显示选项**

	name: String
	route: RouteLocationNormalized

**RouterLinkProps 路由链接选项**

	to: RouteLocationRaw
	replace: Boolean           - replace or push
	activeClass: String		
	ariaCurrentValue:          - 激活时传递的值 "location" | "time" | "page" | "step" | "date" | "true" | "false" 
	custom: Boolean            - 渲染为 <slot> 而非 <a>
	exactActiveClass: String   - 精准匹配时的类

**RouterOptions 原始配置对象**

- `end`
- `history` - 传入通过 API 创建的历史记录对象。
- `linkActiveClass` - String，激活类
- `linkExactActiveClass` - String，精确匹配时激活类 
- `parseQuery`
- `routes: Array<RouteRecordRaw>` - 初始的路由记录数组
- `scrollBehavior` - 滚动行为
- `sensitive`
- `strict`
- `stringifyQuery`

**RouteLocationNormalizedLoaded 当前路由地址实例**

- `fullPath` - 完整的路由地址 URL 编码。
- `path` - pathname 部分，即初始化时 `path` 属性定义部分。
- `hash` - `#` 开头的部分，
- `query` - search 部分，即跟随的参数。
- `matched` - RouteRecordNormalized[]，该地址匹配的路由记录数组。
- `meta` - 携带的元数据
- `name` - 路由名
- `redirectedFrom`
- `params` - 路径参数

**RouteRecordNormalized 当前路由记录**

- `path` - 路由地址
- `redirect` - 重定向路由地址
- `name` - 路由记录名
- `aliasOf` - 作为另一记录的别名
- `children` - 子数组
- `beforeEnter` - 导航守卫
- `meta` - 传递的数据
- `props`
- `components` - 视图

**RouteRecordRaw 原始路由记录**

在 `router options` 中或使用 `router.addRoute()` 时的路由记录类型。

- `path` - String，路由地址。`/`
- `redirect` - `String | Location | Function`，重定向路由地址。
- `name` - 路由名
- `alias` - 别名
- `children` - 路由嵌套
- `beforeEnter(to: Route, from: Route, next: Function) => void`
- `meta` - Any，元数据
- `props` - boolean | Object | Function
- `sensitive` - Boolean，匹配是否区分大小写
- `strict` - Boolean，严格检测 `/`