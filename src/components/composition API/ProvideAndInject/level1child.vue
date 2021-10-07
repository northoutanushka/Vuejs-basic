<template>
  <div>
    name of the com is{{ name }}
    <br />
    <Level2child />
  </div>
</template>

<script>
import { ref } from "vue";
import Level2child from "./level2child.vue";
export default {
  components: { Level2child },
  setup() {
    const name = ref("level 1 child");

    return {
      name,
    };
  },
};
</script>

<style></style>
