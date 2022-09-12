
<script setup>
import { ref } from "vue";
let isShow = ref(false);
</script>

<template>
  <div>
    <button @click="isShow = true">点我弹窗</button>
    <teleport to="body">
      //定位到body
      <div class="mask" v-if="isShow">
        <div class="dialog">
          <h4>我是一个弹窗</h4>
          <h5>内容</h5>
          <h5>内容</h5>
          <h5>内容</h5>
          <button @click="isShow = false">关闭</button>
        </div>
      </div>
    </teleport>
  </div>
</template>

<style>
.dialog {
  width: 300px;
  height: 300px;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: blueviolet;
  margin: 0 auto;
}
.mask {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
