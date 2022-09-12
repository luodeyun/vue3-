<script>
//使用setup的注意事项
import { ref, reactive, watchEffect } from "vue";

export default {
  name: "test5",

  emits: ["hello"],
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        salary: "15k",
      },
    });

    //用处： 如果是比较复杂的业务，发票报销等，那就不许需要去监听其他依赖，只要发生变化，立马重新回调
    //注重逻辑过程，你发生改变了我就重新执行回调，不用就不执行，只执行一次
    watchEffect(() => {
      //这里面你用到了谁就监视谁，里面就发生回调
      const x1 = sum.value;
      console.log("我调用了", x1);
    });
    const add = () => {
      console.log(1);
      sum.value += 1;
    };
    return {
      sum,
      msg,
      add,
      person,
    };
  },
};
</script>
<template>
  {{ sum }}
  <button @click="add">点我+1</button>
</template>