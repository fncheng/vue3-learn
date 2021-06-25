## Composition API

### 被 ref() 包装 的变量

```js
const readersNumber = ref(2);
console.log(readersNumber); // 
```

打印结果：

<img src="https://minimax-1256590847.cos.ap-shanghai.myqcloud.com/img/image-20210420112732017.png" alt="image-20210420112732017" style="zoom:70%;" />

### 被reactive() 包装的变量

```js
const obj = reactive({
  name: 'zs',
  age: 18
})
```

打印结果：

<img src="https://minimax-1256590847.cos.ap-shanghai.myqcloud.com/img/image-20210422110445665.png" alt="image-20210422110445665" style="zoom:67%;" />

```js
setup(prop,context){
	console.log(prop)
  console.log(context)
}
```

打印结果：

<img src="https://minimax-1256590847.cos.ap-shanghai.myqcloud.com/img/image-20210420114211526.png" alt="image-20210420114211526" style="zoom:70%;" />



context：

<img src="https://minimax-1256590847.cos.ap-shanghai.myqcloud.com/img/image-20210420114335981.png" alt="image-20210420114335981" style="zoom:67%;" />



### toRaw()返回原始数据

```js
const obj = toRaw({
  name: 'zs',
  age: 18,
});
console.log(obj); // {name: "zs", age: 18}
```

### toReadonly()包装的变量

toReadonly也会将变量包装成一个Proxy对象



### [watchEffect](https://vue3js.cn/docs/zh/api/computed-watch-api.html#watcheffect)

#### watchEffect与watch❓

- `watchEffect` 不需要指定监听的属性，他会自动的收集依赖， 只要我们回调中引用到了 响应式的属性， 那么当这些属性变更的时候，这个回调都会执行，而 `watch` 只能监听指定的属性而做出变更(v3开始可以同时指定多个)。

- 第二点就是 watch 可以获取到新值与旧值（更新前的值），而 `watchEffect` 是拿不到的。

  ```js
  watch:{
    someValue(newValue,oldValue){
      // ...
    }
  }
  ```

- 第三点是 watchEffect 如果存在的话，在组件初始化的时候就会执行一次用以收集依赖（与`computed`同理），而后收集到的依赖发生变化，这个回调才会再次执行，而 watch 不需要，因为他一开始就指定了依赖。







## 组件通信：

#### 1. provide/inject注入

https://vue3js.cn/docs/zh/guide/composition-api-provide-inject.html