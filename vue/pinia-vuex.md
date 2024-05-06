# 状态管理

**what is state management**

多个视图依赖于同一状态，多个动作更改同一状态的解决方案。

- view 视图，对状态的显示。
- state 状态、数据源，触发视图更新。
- actions 动作，改变状态。

## [Pinia](https://pinia.vuejs.org/zh/)

	$ npm install pinia

**Create** 

```ts
// @/store/index.ts
import { createPinia } from 'pinia'
const pinia = createPinia()
export function seftupStore(app: App<Element>) {
	app.use(pinia)
}
```

**Define**

```ts
// @/store/modules/counter.ts
import { defineStore } from 'pinia'
// Obj 语法
export const useCounterStore = defineStore('counter', {
	state: () => ({ count: 0 }),                                  // 定义数据
	getters: { doubleCount: (state) => state.count * 2 },         // 计算属性
	actions: { increment() { this.count++ } }                     // 定义方法
})

// Func 语法
export const useCounterStore = defineStore('counter', () => {
	const count = ref(0)                                          // 定义数据
	const doubleCount = computed((state) => state.count * 2)      // 计算属性
	function increment() { count.value++ }                        // 定义方法
	return { count, doubleCount, increment }
})
```

**User**

```ts
import { useCounterStore } from '@/store/modules/counter.ts'
const store = useCounterStore()
setTimeout(() => { store.increment() }, 1000)                   // 调用方法
const doubleValue = computed(() => store.doubleCount)           // 绑定计算属性

// 解构：store 是 reactive 对象，通过 storeToRefs 解构
import { storeToRefs } from 'pinia'
const { count, doubleCount } = storeToRefs(store)
const { increment } = store                                     // 方法能直接解构
```

## [Vuex 4](https://vuex.vuejs.org/zh/guide/)