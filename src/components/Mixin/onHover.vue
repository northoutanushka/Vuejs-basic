<template>
  <div>
    <p>the counter value is : {{ counter }}</p>
    <button @mouseover="Increment">counter hover</button>
  </div>
</template>
<script>
import Countermixin from "./counter";
export default {
  mixins: [Countermixin],
};
</script>

<style></style>
