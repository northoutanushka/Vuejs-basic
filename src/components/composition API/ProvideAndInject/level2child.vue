<template>
  <div>
    name of the com is{{ child }}

    inject values are {{ name }} and {{ passtochild2 }} and count value is
    {{ count }}
    <button @click="IncrementCount">child2 click button</button>
  </div>
</template>

<script>
import { inject, toRefs } from "vue";
export default {
  setup() {
    const child = inject("level2name", "defalt value if not found");

    const stateObj = inject("state", {});
    const IncrementCount = inject("IncrementCount");

    return { child, ...toRefs(stateObj), IncrementCount };
  },
};
</script>

<style></style>
