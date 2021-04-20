// Composition API
<template>
  <div>
    <div>{{ readersNumber }}</div>
    <div>{{ book.title }}</div>
    <div>{{ readersNumberComputed }}</div>
    <button @click="readersNumber++">Button</button>
  </div>
</template>

<script>
import { ref, reactive, onMounted, onUpdated, watch, computed } from 'vue';
import useMydata from './useMydata';
export default {
  name: 'HelloWorld',
  /*
    setup watch & computed
   */
  setup() {
    const { readersNumber, book } = useMydata();
    // watch
    watch(readersNumber, (newValue, oldValue) => {
      console.log('oldValue: ', oldValue);
      console.log('newValue: ', newValue);
      console.log(readersNumber);
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
