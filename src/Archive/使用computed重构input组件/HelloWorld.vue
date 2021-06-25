// 使用计算属性重构input
<template>
  <div>
    <input type="text" v-model="value" />
    <!-- 等效于 -->
    <input
      type="text"
      :value="value"
      @input="$emit('update:value', $event.target.value)"
    />
  </div>
</template>

<script>
import { reactive, readonly, ref } from '@vue/reactivity';
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    title: String,
    content: String,
  },
  computed: {
    value: {
      get() {
        console.log('get');
        return this.title;
      },
      set(value) {
        console.log('set');
        this.$emit('update:title', value);
      },
    },
  },
  setup(props, context) {
    const msg = ref(1);
    const STATUS = readonly({ status: 200 });
    const obj = reactive({
      name: 'zs',
      age: 18,
    });
    console.log(123);
    console.log(456);
    return { msg, STATUS, obj };
  },
  created() {
    console.log(this.msg);
    console.log(this.STATUS);
    console.log(this.obj);
    this.STATUS.status = 300; // failed readonly
  },
};
</script>
