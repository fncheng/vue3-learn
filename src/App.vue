<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <button @click="msg = '123'">Change msg</button>
  <HelloWorld v-model:title="pageTitle" v-model:content="content" />
  <div>{{ pageTitle }}</div>
  <div>{{ content }}</div>
  <button @click="handleClick">Button</button>
  <!-- <HelloWorld v-if="isShow" /> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld: () =>
      import(/* webpackChunkName: "List" */ './components/HelloWorld.vue'),
  },
  data() {
    return {
      msg: 'Hello Vue 3.0 + Vite',
      pageTitle: '',
      content: '',
      isShow: false,
    };
  },
  methods: {
    handleClick() {
      console.log('click');
      this.isShow = true;
    },
  },
};
</script>
