# [React](https://react.docschina.org/learn)

    $ npm install react react-dom

**[React Router](https://reactrouter.com/en/main)**

    $ npm install react-router-dom localforage match-sorter sort-by

**项目结构**
```
src
|- main.tsx
|- routes
    |- root.tsx
```

## 程序入口 `./main.tsx`
```tsx
import * as React from "react";
import * as ReactDOM from "react-dom/client"; // or 'react-dom/server'
import { createBrowserRouter, RouterProvider, } from "react-router-dom";
import Root from "./routes/root";

// 创建路由
const router = createBrowserRouter([
  {
    path: "/",
    element: <Root />,
    children: [ { path: 'children/:childrenId', element: <Children /> } ]
  }  
])

// 创建 React 实例并挂载到 DOM
ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
);
```

## 根组件 `./routes/root.tsx`

```tsx
import { Outlet, Link } from "react-router-dom";
export default function Root() {
  return (
    <>
      {/* 路由导航组件*/}
      <Link to={`contacts/1`}></Link>
      {/* 路由显示组件*/}
      <Outlet />
    </>
  );
}

// 定义子组件
function Children() {

  const [count, setCount] = React.useState(0)                 // 引入状态和更新函数
  function handleClick() { setCount(count + 1) }              // 定义事件，调用状态更新函数

  // 定义列表和项
  const items = [{ title: '', id: 1 }, { title: '', id: 2 }]  
  const lists = items.map( item => <li key={ item.id }>{ item.title }</li> )

  // 条件渲染
  if (isLogin) { content = <Welcome /> } else { content = <Login /> }

  // '()' JSX 语法, '{}' JS 语法
  return (
    <div 
      className='' 
      style={ {width: user.width} } 
      count={ count } 
      onClick={ handleClick } 
    >
      { 
        /* 表达式渲染 */
        isLogin ? <Login /> : <Welcome /> 
      }
    </div>
  )
}
```

## React

**Hook**

- `use` - 定义读取资源如 Promise 和上下文值
- `useState` - 定义状态，定义更新状态函数。
- `useReducer` - 定义状态，reducer 函数中带更新逻辑的变量。
- `useContext` - 接收祖先数据。
- `useRef` - 定义无需渲染的数据，不会重新渲染组件
- `useImperativeHandle` - 定义从组件中暴露的 Ref
- `useEffect( () => {} )` - 混入外部代码
- `useLayoutEffect` - 混入外部代码，在浏览器重新绘制屏幕前执行
- `useInsertionEffect` -混入外部代码， 在 React 对 DOM 进行更改之前触发
- `useMemo( () => {} )` - 性能优化，若数据未改变则重用计算结果。
- `useCallback` - 性能优化
- `useTransition` - 性能优化，定义为非阻塞，允许其他更新中断。
- `useDeferredValue` - 性能优化，定义为非关键，允许其他部分先更新。
- `useDebugValue` 
- `useId`
- `useSyncExternalStore` 

**API**

- `createContext` - 创建 context 提供给子组件 `useContext` 使用。  
- `forwardRef` - 将 DOM 节点作为 Ref 暴露给父。
- `lazy` - 懒加载
- `memo` - props 没有变化时跳过重新渲染。
- `startTansition` - 定义为非关键的状态更新。

**Components**

- `<Fragment>`、`<>...</>` - 定义片段
- `<Profiler>` - 定义性能分析。
- `<Suspense>` - 定义子组件加载的后备方案。
- `<React.StrictMode>` - 定义仅用于开发环境的检测。

## React DOM API

**react-dom**

- `createPortal`
- `flushSync`
- `prefetchDNS` - 定义预先加载
- `preconnect` - 定义预先加载
- `preload` - 定义预先加载
- `preloadModule` - 定义预先加载
- `preinit` - 定义预先加载
- `preinitModule` - 定义预先加载

**react-dom/client**

- `createRoot(domNode, options?)` - 绑定到 DOM
  + `render(reactNode)` - 绑定的 React Node
  + `root.unmount()` - 销毁 React Node
- `hydrateRoot(domNode, reactNode)` - 绑定到 DOM, 通过 react-dom/service 创建的 reactNode

**react-dom/service**

- `renderToPipeableStream` - 将 React 渲染为 Node.js 流。
- `renderToStaticNodeStream` - 将非交互 React 渲染为 Node.js 流。
- `renderToReadableStream` - 将 React 渲染为 web 流。
- `renderToString` - 将 React 渲染为字符串。
- `renderToStaticMarkup` - 将非交互式 React 渲染为字符串。

## React Router DOM API

    import { createBrowserRouter } from "react-router-dom"

**createBrowserRouter 创建路由**

```ts
function createBrowserRouter(
  routes: RouteObject[],
  opts?: {
    basename?: string;
    future?: FutureConfig;
    hydrationData?: HydrationState;
    window?: Window;
  }
): RemixRouter;
```

**route 路由对象**

```ts
interface RouteObject {
  path?: string;
  index?: boolean;
  children?: React.ReactNode;
  caseSensitive?: boolean;
  id?: string;
  loader?: LoaderFunction;
  action?: ActionFunction;
  element?: React.ReactNode | null;
  hydrateFallbackElement?: React.ReactNode | null;
  errorElement?: React.ReactNode | null;
  Component?: React.ComponentType | null;
  HydrateFallback?: React.ComponentType | null;
  ErrorBoundary?: React.ComponentType | null;
  handle?: RouteObject["handle"];
  shouldRevalidate?: ShouldRevalidateFunction;
  lazy?: LazyRouteFunction<RouteObject>;
}
```

**`<RouterProvider>`**

路由入口,挂载点

```ts
declare function RouterProvider(
  props: RouterProviderProps
): React.ReactElement;

interface RouterProviderProps {
  fallbackElement?: React.ReactNode;
  router: Router;
  future?: Partial<FutureConfig>;
}
```

**Components `<Link>`**

链接,跳转路由

```ts
declare function Link(props: LinkProps): React.ReactElement;

interface LinkProps
  extends Omit<
    React.AnchorHTMLAttributes<HTMLAnchorElement>,
    "href"
  > {
  to: To;
  preventScrollReset?: boolean;
  relative?: "route" | "path";
  reloadDocument?: boolean;
  replace?: boolean;
  state?: any;
  unstable_viewTransition?: boolean;
}

type To = string | Partial<Path>;

interface Path {
  pathname: string;
  search: string;
  hash: string;
}
```

**Components `<Outlet>`**

父路由元素中显示子路由

```ts
interface OutletProps {
  context?: unknown;
}
declare function Outlet(
  props: OutletProps
): React.ReactElement | null;
```