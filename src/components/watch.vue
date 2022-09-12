<template>
  <h1>当前求和为： {{ sum }}</h1>
  <button @click="sum++">点我+1</button>
  <hr />
  <h1>当前信息为： {{ msg }}</h1>
  <button @click="msg += '!'">修改信息</button>
  <hr />
  <h2>姓名： {{ person.name }}</h2>
  <h2>年龄： {{ person.age }}</h2>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
</template>

<script>
//使用setup的注意事项
import { watch, ref, reactive } from "vue";

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
    //由于这里的this是指的是undefined，所以使用箭头函数
    //情况一：监视ref所定义的一个响应式数据
    watch(sum, (newValue, oldValue) => {
      console.log("新的值", newValue);
      console.log("旧的值", oldValue);
    });

    //情况二：监视ref所定义的多个响应式数据
    watch(
      [sum, msg],
      (newValue, oldValue) => {
        console.log("新的值", newValue); //['sum的newValue', 'msg的newValue']
        console.log("旧的值", oldValue); //['sum的oldValue', 'msg的oldValue']
      },
      { immediate: true, deep: true }
    ); //这里vue3的deep是有点小问题的，可以不用deep

    //情况三：监视reactive定义的所有响应式数据,
    //1.此处无法获取正确的oldValue（newValue与oldValue是一致值）,且目前无法解决
    //2.强制开启了深度监视（deep配置无效）
    watch(person, (newValue, oldValue) => {
      console.log("新的值", newValue);
      console.log("旧的值", oldValue);
    });

    //情况四：监视reactive对象中某一个属性的值，
    //注意： 这里监视某一个属性的时候可以监听到oldValue
    watch(
      () => person.name,
      (newValue, oldValue) => {
        console.log("新的值", newValue);
        console.log("旧的值", oldValue);
      }
    );

    //情况五：监视reactive对象中某一些属性的值
    watch([() => person.name, () => person.age], (newValue, oldValue) => {
      console.log("新的值", newValue);
      console.log("旧的值", oldValue);
    });

    //特殊情况: 监视reactive响应式数据中深层次的对象，此时deep的配置奏效了
    watch(
      () => person.job,
      (newValue, oldValue) => {
        console.log("新的值", newValue);
        console.log("旧的值", oldValue);
      },
      { deep: true }
    ); //此时deep有用

    return {
      sum,
      msg,
      person,
    };
  },
};
</script>
