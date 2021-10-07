<template>
  <div>
    my hobby is {{ hobby }}
    <p v-if="anyOther">other hobby is {{ another }}</p>
    <button @click="change">click to change the hobby</button>
    <button @click="changeAnother">click</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";
export default {
  setup() {
    const hobby = ref("singing");
    const state = reactive({
      another: "cooking",
      anyOther: false,
    });

    function change() {
      hobby.value = "dancing";
    }

    function changeAnother() {
      state.anyOther = !state.anyOther;
    }

    //if wants to written only state then ... is not required but if return {} k andr likhna h to object k andr object return nh hoga so use ... to extract
    //the keys as a list

    return {
      hobby,
      change,
      changeAnother,
      ...toRefs(state),
    };
  },
};
</script>

<style></style>
