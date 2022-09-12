
<template>
  <h2>姓名： {{ name2 }}</h2>
  <h2>年龄： {{ person.age }}</h2>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
</template>

<script>
//使用setup的注意事项
import { reactive, toRef } from "vue";

export default {
  name: "test9",
  setup() {
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        salary: "15k",
      },
    });
    //toRef
    const name2 = toRef(person, "name"); //第一个参数是对象，第二个参数是键名
    console.log("toRef转变的是", name2); //ref定义的对象

    //toRefs,批量处理对象的所有属性
    //const x  = toRefs(person)
    //console.log('toRefs转变的是',x); //是一个对象
    return {
      person,
      name2,
    };
  },
};
</script>
