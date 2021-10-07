<template>
  <div>
    <p>current machine is {{ name }}</p>
    <p>current machine model is {{ model }}</p>
    <button @click="change">click to change the machine name and model</button>
  </div>
</template>

<script>
import { ref, watch } from "vue";
export default {
  setup() {
    const name = ref("desktop");
    const model = ref("new");

    function change() {
      name.value = "laptop";
      model.value = "old";
    }

    watch([name, model], (newValue) => {
      console.log(newValue[0]);
      console.log(newValue[1]);
    });
    return {
      name,
      model,
      change,
    };
  },
};
</script>

<style></style>
