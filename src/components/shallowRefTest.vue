<template>
  <div>{{ obj.count }} ---</div>
  <div>{{ obj2.count }} ---</div>
</template>
<script>
import { shallowRef, shallowReactive } from "vue";

export default {
  setup() {
    let obj = shallowRef({ count: 1 });
    let obj2 = shallowReactive({ count: 1 });
    setTimeout(() => {
      // shallowRef
      // obj.value.count == 2; // 这时界面是不会有变化的
      // obj.value = {
      //   // 界面会有变化
      //   count: 2,
      // };
      // shallowReactive
      obj2.count = 2;
      console.log(obj2);
    }, 1500);
    return { obj, obj2 };
  },
};
</script>