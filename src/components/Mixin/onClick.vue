<template>
  <div>
    <p>the counter value is : {{ counter }}</p>
    <button @click="Increment">counter click</button>
  </div>
</template>
<script>
import Countermixin from "./counter";
export default {
  mixins: [Countermixin],
};
</script>

<style></style>
