<template>
  <!-- <Ref></Ref> -->
  <!-- <Reactive></Reactive> -->
  <!-- <Computed /> -->
  <!-- <Watch title="12334"></Watch> -->
  <!-- <WatchEffect></WatchEffect> -->
  <!-- <lifeCycle> </lifeCycle> -->
  <!-- <shallowRefs></shallowRefs> -->
  <!-- <readonly /> -->
  <!-- <toraw /> -->
  <!-- <Father /> -->
  <!-- <Transitions /> -->
  <!-- <TelePorts /> -->
  <Suspenses />
</template>

<script>
// import Ref from "./components/refTest.vue";
// import Reactive from "./components/reactive.vue";
// import Computed from "./components/computed.vue";
// import Watch from "./components/watch.vue";
// import WatchEffect from "./components/watchEffectTest.vue";
// import lifeCycle from "./components/lifeCycle.vue";
// import shallowRefs from "./components/shallowRefTest.vue";
// import toRef from "./components/toRef.vue";
// import readonly from "./components/readonly.vue";
// import toraw from "./components/toraw.vue";
// import Father from "./components/provide/fathers.vue";
// import Transitions from "./components/transition.vue";
// import TelePorts from "./components/telePort.vue";
import Suspenses from "./components/suspense.vue";
export default {
  components: {
    // Ref,
    // Reactive,
    // Computed,
    // Watch,
    // WatchEffect,
    // lifeCycle,
    // toRef,
    // shallowRefs,
    // readonly,
    // toraw,
    // Father,
    // Transitions,
    // TelePorts,
    Suspenses,
  },
  name: "App",
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
