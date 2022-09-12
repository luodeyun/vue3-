
<script setup>
import { inject, toRefs } from "vue";
let car = inject("car"); //拿到父组件的数据
const { name, price } = toRefs(car);
</script>

<template>
  <div class="app3">
    <h3>我是孙组件</h3>
    <p>{{ name }}-{{ price }}</p>
  </div>
</template>
<style>
.app3 {
  background-color: rgb(231, 184, 56);
  padding: 10px;
  box-sizing: border-box;
}
</style>
