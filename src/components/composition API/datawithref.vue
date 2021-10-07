<template>
  <div>
    <p>my name is :{{ namevavlue }}</p>
    <p>my name is :{{ msg }}</p>
  </div>
</template>

<script>
// to replace data with ref --refs only use primitive values
import { ref } from "vue";
export default {
  setup() {
    const name = ref("Composition API");
    const welcome = ref(`welcome to ${name.value}`);
    //return the object with key and value and if the name of key and value is same then use single word only
    return {
      namevavlue: name,
      msg: welcome,
    };
  },
};
</script>

<style></style>
