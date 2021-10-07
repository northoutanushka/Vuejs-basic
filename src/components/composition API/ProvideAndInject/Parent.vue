<template>
  <div>
    name of the com is{{ name }} and count value from parent is {{ count }}
    <button @click="IncrementCount">parent click button</button>
    <br />
    <Level1child />
  </div>
</template>

<script>
import { provide, reactive, ref, toRefs } from "vue";
import Level1child from "./level1child.vue";
export default {
  components: { Level1child },
  setup() {
    //usinf ref
    const name = ref("parent component ref");

    provide("level2name", "comp inject from parent comp");

    //using reactive
    const state = reactive({
      name: "parent component reactive",
      passtochild2: true,
      count: 0,
    });

    function IncrementCount() {
      state.count++;
    }

    provide("state", state);
    provide("IncrementCount", IncrementCount);
    return {
      name,
      ...toRefs(state),
      IncrementCount,
    };
  },
};
</script>

<style></style>
