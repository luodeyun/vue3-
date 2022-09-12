<template>
  <button @click="show = !show">切换</button>
  <Transition>
    <p v-if="show">HelloWord</p>
  </Transition>

  <!-- /**
//当一个 <Transition> 组件中的元素被插入或移除时，会发生下面这些事情
1.Vue 会自动检测目标元素是否应用了 CSS 过渡或动画。如果是，则一些 CSS 过渡 class 会在适当的时机被添加和移除
2.如果有作为监听器的 JavaScript 钩子，这些钩子函数会在适当时机被调用
3.如果没有探测到 CSS 过渡或动画、也没有提供 JavaScript 钩子，那么 DOM 的插入、删除操作将在浏览器的下一个动画帧后执行
*/

//针对CSS 的过渡效果
/**
1.v-enter-from：进入动画的起始状态。在元素插入之前添加，在元素插入完成后的下一帧移除。
2.v-enter-active：进入动画的生效状态。应用于整个进入动画阶段。在元素被插入之前添加，在过渡或动画完成之后移除。这个 class 可以被用来定义进入动画的持续时间、延迟与速度曲线类型
3.v-enter-to：进入动画的结束状态。在元素插入完成后的下一帧被添加 (也就是 v-enter-from 被移除的同时)，在过渡或动画完成之后移除。
4.v-leave-from：离开动画的起始状态。在离开过渡效果被触发时立即添加，在一帧后被移除
5.v-leave-active：离开动画的生效状态。应用于整个离开动画阶段。在离开过渡效果被触发时立即添加，在过渡或动画完成之后移除。这个 class 可以被用来定义离开动画的持续时间、延迟与速度曲线类型。
6.v-leave-to：离开动画的结束状态。在一个离开动画被触发后的下一帧被添加 (也就是 v-leave-from 被移除的同时)，在过渡或动画完成之后移除。
*/ -->
</template>
<script>
import { ref } from "vue";
export default {
  setup() {
    let show = ref(false);
    return { show };
  },
};
</script>
<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>