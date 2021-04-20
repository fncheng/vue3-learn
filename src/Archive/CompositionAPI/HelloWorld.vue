// Composition API
<template>
  <el-checkbox-group v-model="mydata.list[0].checked">
    <el-checkbox label="复选框 A"></el-checkbox>
    <el-checkbox label="复选框 B"></el-checkbox>
    <el-checkbox label="复选框 C"></el-checkbox>
    <el-checkbox label="禁用"></el-checkbox>
    <el-checkbox label="选中且禁用"></el-checkbox>
  </el-checkbox-group>
  <div>{{ readersNumber }} {{ book.title }}</div>
</template>

<script>
import { ref, reactive, onMounted, onUpdated } from 'vue';
export default {
  name: 'HelloWorld',
  /*
    setup在beforeCreate之前调用
   */
  setup() {
    // const mydata = ref([]);
    const { mydata, readersNumber, book } = useMydata();
    onMounted(() => {
      console.log('onmounted');
    });
    onUpdated(() => {
      console.log('onUpdated');
    });
    return { mydata, readersNumber, book };
  },
  data() {
    return {
      checkList: [],
    };
  },
  mounted() {
    console.log('mounted');
  },
  updated() {
    console.log(this.mydata.list[0].checked);
  },
  errorCaptured: (err, vm, info) => {
    console.log('info: ', info);
  },
  renderTracked({ key, target, type }) {
    console.log('{key,target,type}: ', { key, target, type });
  },
};
function useMydata() {
  const mydata = reactive({
    list: [
      {
        name: 'zs',
        age: 18,
        checked: [],
      },
    ],
  });
  const readersNumber = ref(2);
  const book = reactive({ title: 'Vue 3 Guide' });
  return { mydata, readersNumber, book };
}
</script>
