// Composition API
<template>
  <div>
    <div>{{ readersNumber }}</div>
    <div>{{ book.title }}</div>
    <div>{{ readersNumberComputed }}</div>
    <div>props.msg: {{ msg }}</div>
    <button @click="readersNumber++">Button</button>
  </div>
</template>

<script>
import {
  ref,
  reactive,
  onMounted,
  onUpdated,
  watch,
  computed,
  toRefs,
} from 'vue';
import useMydata from './useMydata';
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  /*
    setup props & context
   */
  setup(props, context) {
    console.log('context: ', context);
    console.log('props: ', props);
    const { readersNumber, book } = useMydata();
    // props
    // const { msg } = props;  ❌ 使用es6解构会破坏props的响应性
    // ✅ use toRefs API
    const { msg } = toRefs(props);
    console.log(msg);
    // watch
    watch(msg, (newValue, oldValue) => {
      console.log('oldValue: ', oldValue);
      console.log('newValue: ', newValue);
      console.log(msg);
    });
    const readersNumberComputed = computed(() => {
      return '123' + readersNumber.value;
    });
    onMounted(() => {
      console.log('onmounted');
    });
    onUpdated(() => {
      console.log('onUpdated');
    });
    return { readersNumber, book, readersNumberComputed };
  },
};
</script>
