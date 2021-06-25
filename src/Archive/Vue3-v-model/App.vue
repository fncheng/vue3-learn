<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <button @click="msg = '123'">Change msg</button>
  <HelloWorld v-model:title="pageTitle" v-model:content="content" />
  <div>{{ pageTitle }}</div>
  <div>{{ content }}</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      msg: 'Hello Vue 3.0 + Vite',
      pageTitle: '',
      content: '',
    };
  },
};
</script>
