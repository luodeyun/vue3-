<template>
  {{ obj.name }}
</template>
<script>
import { reactive } from "vue";
export default {
  setup() {
    let obj = reactive({ name: "ldy" });
    setTimeout(() => {
      obj.name = "ldh";
    }, 1500);
    return { obj };
  },
};
</script>