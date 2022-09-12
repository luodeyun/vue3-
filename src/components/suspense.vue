<script setup>
import { defineAsyncComponent } from "vue"; //引入异步组件
let ChildVue;
setTimeout(() => {
  ChildVue = defineAsyncComponent(() => import("./provide/fathers.vue")); //这叫做动态引入
}, 2000);

// import ChildVue from "./provide/fathers.vue"; //静态引入
//这种引入叫做异步引入，如果app不出来的话，那么Child组件也不会引入进来，有一个先后顺序

// import ChildVue from './components/Child.vue'; //静态引入
// 得等，等所有的组件加载完成之后app才会一起出现

/**
 * Suspense这个标签，底层就内置了插槽，就可以解决异步引入有时候刷新先后出来慢的问题
 * v-slot:default 表示默认的输出组件
 * v-slot:fallback 表示如果页面加载的慢了，会优先展示这个内容，有点像刷新页面的时候数据回来的慢了，就加载一会儿
 */
/**
 * 还有一种方法就是在子组件中，setup返回一个promise对象，这里之所以可以使用setup返回promise的原因
 * 是: 我们引入的是异步组件且使用了<Suspense></Suspense>
 *
 */
</script>

<template>
  <div class="app">
    <h3>我是父组件</h3>
    <!-- <ChildVue></ChildVue> -->
    <Suspense>
      <template v-slot:default>
        <div>
          <ChildVue></ChildVue>
        </div>
      </template>
      <template v-slot:fallback>
        <h3>稍等，加载中....</h3>
      </template>
    </Suspense>
  </div>
</template>

<style>
.app {
  background-color: gray;
  padding: 10px;
  box-sizing: border-box;
}
</style>
