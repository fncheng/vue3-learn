// v-model
<template>
  <div>
    <input type="text" :title="title" @input="handleInput" :content="content" />
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    title: String,
    content: String,
  },
  methods: {
    handleInput(e) {
      console.log(e.target.value);
      this.$emit('update:title', e.target.value);
      this.$emit('update:content', e.target.value + '123');
    },
  },
  setup(props, context) {},
};
</script>
