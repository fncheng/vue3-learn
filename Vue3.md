## Vue3

### Composition API

被 ref() 包装 的变量

```js
const readersNumber = ref(2);
console.log(readersNumber); // 
```

打印结果：

<img src="/Users/cheng/Library/Application Support/typora-user-images/image-20210420112732017.png" alt="image-20210420112732017" style="zoom:70%;" />



```js
setup(prop,context){
	console.log(prop)
  console.log(context)
}
```

打印结果：

<img src="/Users/cheng/Library/Application Support/typora-user-images/image-20210420114211526.png" alt="image-20210420114211526" style="zoom:70%;" />



context：

<img src="/Users/cheng/Library/Application Support/typora-user-images/image-20210420114335981.png" alt="image-20210420114335981" style="zoom:67%;" />