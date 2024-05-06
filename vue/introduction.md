# 响应式原理与声明式语法

## 声明式

Vue 支持声明式地将组件实例的数据绑定到呈现的 DOM 上，称为**模板语法**。

- 支持双括号文本插值。 `{{}}`
- 支持 JS 表达式。必须是能够被求值的，即能够合法写在 `return` 后面的。
- 以 v- 开头的指令语法，`v-[dir]:[dir-arg]="doSomething"`

## 响应式原理

原生 Javascript 变量变化无法直接触发视图更新，</br>
Vue 通过 `ref()` 和 `reactive()` 代理原生 Javascript 变量，实现视图和数据**双向绑定**。

	const valueRef = ref('value')
	console.log(valueRef.value)     => 'value'

调用 `ref()` 时将创建一个 objRef 对象，该对象使用 getter/setter 劫持一个 `.value` 属性。</br>
在 `reactive()` 中通过创建 Proxy 对象实现。
```javascript
function ref(value) {
  const objRef = {
    get value() {
      track(objRef, 'value')
      return value
    },
    set value(newValue) {
      value = newValue
      trigger(objRef, 'value')
    }
  }
}
````
当这个 objRef 被获取时，检查获取它的**副作用**`activeEffect`，<br/>
将这些副作用保存到 objRef 的副作用列表 `effects`。
```javascript
let activeEffect
function track(target, key){
  if (activeEffect) {
    const effects = getSubscribersForProperty(target, key)
    effects.add(activeEffect)
  }
}
```
当这个 objRef 被设置时，获取它的副作用列表 `effects`，<br/>
使用设置的新值遍历调用列表中的所有副作用，即更新所有值。
```javascript
function trigger(target, key) {
  const effects = getSubscribersForProperty(target, key)
  effects.forEach((effect) => effect())
}
```