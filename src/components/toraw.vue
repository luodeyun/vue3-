<template>
  {{ person.name }}
  <button @click="showRawPerson">
    showRawPerson{{ p.age }} ----{{ person.age }}
  </button>
  <button @click="addCar">markRaw</button>
</template>
<script>
import { reactive, toRaw, markRaw, nextTick } from "vue";
export default {
  setup() {
    let person = reactive({
      name: "张三",
      age: 1,
    });
    let p = { age: 1 };
    function showRawPerson() {
      p = toRaw(person); // 创建一个普通对象 对这个普通对象操作并不会影响源响应式对象
      p.age++;
      //   person.age += 2;
      nextTick(() => {
        console.log(p, person.age);
        person.age += 10;
      });
    }
    function addCar() {
      let car = { name: "奔驰" };
      person.car = markRaw(car); //一旦这么做时候，他就永远不能当成响应式数据去做了
      console.log(person);
    }
    return { showRawPerson, addCar, person, p };
  },
};
</script>