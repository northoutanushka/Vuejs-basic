<template
  ><div>
    {{ fulrefLName }}
    <br />
    {{ reactFullName }}
  </div>
</template>

<script>
import { computed, ref, reactive, toRefs } from "vue";
export default {
  //with refs
  setup() {
    const refFName = ref("abc");
    const refLName = ref("xyz");

    const fulrefLName = computed(function() {
      return `first name is ${refFName.value} and last name is ${refLName.value}`;
    });

    //with reactive
    const name = reactive({
      reactFName: "abc",
      reactLName: "xyz",
    });

    const reactFullName = computed(function() {
      return `first name is ${name.reactFName} and last name is ${name.reactLName}`;
    });

    return {
      refFName,
      refLName,
      fulrefLName,
      ...toRefs(name),
      reactFullName,
    };
  },
};
</script>

<style></style>
