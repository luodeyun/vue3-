<template>obj --- {{ obj.count }} person --- {{ person.count }}</template>
<script>
import { readonly, ref } from "vue";
export default {
  setup() {
    let obj = ref({ count: 1 });
    let person = readonly(obj);
    obj.value.count = 2;
    person.value.count = 3;
    return { obj, person };
  },
};
</script>