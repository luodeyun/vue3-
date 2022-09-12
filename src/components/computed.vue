<template>
  <h1>一个人的信息</h1>
  <div>
    姓： <input type="text" v-model="person.firstName" /> 名：<input
      type="text"
      v-model="person.lastName"
    />
    <div>
      <span>简名：{{ person.smallName }}</span> <br />
      <span>全名：{{ person.fullName }}</span>
    </div>
  </div>
</template>
  <script>
import { computed, reactive } from "vue";

export default {
  name: "test4",
  setup() {
    let person = reactive({
      firstName: "张",
      lastName: "三",
    });
    //简写形式
    person.smallName = computed(() => {
      return person.firstName + "-" + person.lastName;
    });

    //完全形态
    person.fullName = computed({
      get() {
        console.log("调用get");
        return person.firstName + "*" + person.lastName;
      },
      set(value) {
        console.log("调用set");
        const nameArr = value.split("*");
        person.firstName = nameArr[0];
        person.firstName = nameArr[1];
      },
    });
    return {
      person,
    };
  },
};
</script>