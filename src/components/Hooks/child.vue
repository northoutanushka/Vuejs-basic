<template>
  <h2>child component</h2>
</template>

<script>
export default {
  beforeCreated() {
    console.log("child before created");
  },
  created() {
    console.log("child created");
  },
  beforeMount() {
    console.log("child before mounted");
  },
  mounted() {
    console.log("child mounted");
  },
  beforeUpdate() {
    console.log("child before update");
  },
  updated() {
    console.log("child updated");
  },
  beforeUnmount() {
    console.log("child before unmount");
  },
  unmounted() {
    console.log("child unmounted");
  },
};
</script>

<style></style>
