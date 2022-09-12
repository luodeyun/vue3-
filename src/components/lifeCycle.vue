
<template>
  <h1>生命周期</h1>
  <p>当前求和为： {{ sum }}</p>
  <button @click="sum++">加一</button>
</template>

<script>
//使用setup的注意事项
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

export default {
  name: "test7",
  setup() {
    let sum = ref(0);
    //通过组合式API的形式去使用生命周期钩子
    /**
     * beforeCreate 和  created 这两个生命周期钩子就相当于 setup 所以，不需要这两个
     *
     * beforeMount   ===>  onBeforeMount
     * mounted       ===>  onMounted
     * beforeUpdate  ===>  onBeforeUpdate
     * updated       ===>  onUpdated
     * beforeUnmount ===>  onBeforeUnmount
     * unmounted     ===>  onUnmounted
     */
    console.log("---setup---");
    onBeforeMount(() => {
      console.log("---onBeforeMount---");
    });
    onMounted(() => {
      console.log("---onMounted---");
    });
    onBeforeUpdate(() => {
      console.log("---onBeforeUpdate---");
    });
    onUpdated(() => {
      console.log("---onUpdated---");
    });
    onBeforeUnmount(() => {
      console.log("---onBeforeUnmount---");
    });
    onUnmounted(() => {
      console.log("---onUnmounted---");
    });
    return {
      sum,
    };
  },
  //这种是外层的写法，如果想要使用组合式api的话需要放在setup中
  beforeCreate() {
    console.log("---beforeCreate---");
  },
  created() {
    console.log("---created---");
  },
  beforeMount() {
    console.log("---beforeMount---");
  },
  mounted() {
    console.log("---mounted---");
  },
  beforeUpdate() {
    console.log("---beforeUpdate---");
  },
  updated() {
    console.log("---updated---");
  },
  //卸载之前
  beforeUnmount() {
    console.log("---beforeUnmount---");
  },
  //卸载之后
  unmounted() {
    console.log("---unmounted---");
  },
};
</script>