
<script setup>
import { reactive, toRefs, provide } from "vue";
import ChildVue from "./childs.vue";

let car = reactive({
  name: "奔驰",
  price: "40w",
});
let changeCar = () => {
  car.name = "宝马";
  car.price = "60w";
};
provide("car", car); //给自己的后代组件传递数据
const { name, price } = toRefs(car);
</script>
<template>
  <div class="app">
    <h3>我是父组件, {{ name }}--{{ price }}</h3>
    <button @click="changeCar">换辆车</button>
    <ChildVue></ChildVue>
  </div>
</template>
<style>
.app {
  background-color: gray;
  padding: 10px;
  box-sizing: border-box;
}
</style>
