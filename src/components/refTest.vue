
<template>
  {{ obj }}
</template>
<script >
// import { ref } from "vue";
export default {
  setup() {
    let obj = 2;
    setTimeout(() => {
      obj = 1;
      console.log(obj);
    }, 1500);
    // 不使用ref的情况
    // let obj = ref(2);
    // setTimeout(() => {
    //   obj.value = 1;
    //    console.log(obj.value);
    // }, 1500);
    return { obj };
  },
};
</script>
