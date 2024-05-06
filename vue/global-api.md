# 全局 API

**创建 Vue 实例**

	Vue.createApp(Component, Props)

- Component - 根实例对象形式的组件选项。
- Props - 根实例中定义的 props

**创建 Vue 实例 (SSR 激活模式)**

	Vue.createSSRApp()

**挂载 Vue 实例**

	app.mount(rootContainer)

- rootContainer - 真实 DOM 或 CSS 选择器指定的元素。`#app`

**卸载已挂载的 Vue 实例**

	app.unmount()

**等待 DOM 更新后执行回调**

	Vue.nextTick(Handler)

**当前 vue 版本号**

	import { version } from 'vue'
	const version = app.version

**配置对象**

`app.config` 属性是表示当前 Vue 实例配置选项的对象，它有以下键：

- `errorHandler ` - Function，指定的全局错误处理函数。
- `warnHandler` - Function，指定的全局警告处理函数。
- `performance` - Boolean，开启性能跟踪。
- `compilerOptions` - 配置运行时编译器选项。
- `optionMergeStrategies` - 义自定义组件选项的合并策略的对象。
- `globalProperties` - 注册一个能够被所有后代组件访问的全局 property 对象
	+ 注册：`app.config.globalProperties.msg = 'hello'`
	+ 使用：`mounted() { console.log(this.msg) }`

**提供类型提示帮助函数**

	Vue.defineComponent()

**定义异步组件**

	Vue.defineAsyncComponent()

**自定义元素类的构造函数**

	Vue.defineCustomElement()

**mixins or extends（不推荐）**

**混入**与**继承**将定义好的组件选项合并到组件中，它们的用法一样只是表述不同。

## 安装插件

调用插件提供的 install() 方法并将插件安装到 Vue 实例。

	app.use(plugin, ...options)

- `plugin` - 引入的 Function 或 Object 形式的插件。
- `options` - 插件的初始化选项对象，作为参数传入 install() 方法。

**install 方法**

插件是能够添加全局功能的代码块，它必须作为或提供 install() 方法给 Vue 调用并安装。 

install 方法定义插件注入 Vue 的组件、指令、资源、全局方法与全局属性。
```javascript
const myPlugin = {
  install(app, options) {
    app.component();
    app.directive();  
    app.provide();
    app.config.globalProperties.$[methods | attribute]
  }
}
```
## 依赖"供给"与"注入"

在 Vue 根实例"供给"一个值，它的所有组件实例都可以通过 inject 调用。（全局供给）

	app.provide(key, value)

- `key` - `InjectionKey<T>`、`symbol`、`string`，第一个参数作为"供给"的键。
- `value` - `T`，第二个参数作为注入的值。

在组件中定义"供给"使它的后代组件可以使用（局部供给）

	provide: { key: value }

注入到组件实例。

	inject: ['key']

## 组件注册

全局注册组件

	app.component("my-component", Component)

只传入组件名时，返回已经注册的组件。

	const MyComponent = app.component('my-component')

局部注册组件

	components: {"myComponent": Component}

## 自定义指令

用于重用 DOM 的访问逻辑，应该尽量避免。

全局注册自定义指令

	app.directive('my-directive', Directive)

只传入指令名时，返回已经注册的指令。

	const myDirective = app.directive('my-directive')

局部注册自定义指令

	directives: { myDirective: Directive }

### 定义 Directive

**钩子函数**

自定义指令钩子与生命周期钩子对应。

- `created(el, binding, vnode, prevVnode){}` - 创建完成立即调用。
- `beforeMount` - 挂载 DOM 前调用。
- `mounted` - 挂载 DOM 完成后调用。
- `beforeUpdate` - 更新前调用。
- `updated` - 更新完成后调用。
- `beforeUnmount` - 卸载前调用。
- `unmounted` - 卸载完成后调用。

**参数**

- `el` - 表示指令绑定的元素。
- `binding` - Object
	+ `value` - 传递的值，如：`v-myDirective="value"`
	+ `oldValue` - 记录的更新前的 value，`beforeUpdate`、`updated` 可用。
	+ `arg` - 传递的参数，如：`v-myDirective:arg`
	+ `modifiers` - 传递的修饰符对象，如：`v-myDirective.foo.bar` 即为 `{ foo: true, bar: true }`
	+ `instance` - 使用该指令的组件实例。
	+ `dir` - 指令的定义对象。
- `vnode` - 代表绑定元素的底层 VNode。
- `preVnode` - 更新前的 VNode，`beforeUpdate`、`updated` 可用。