<template>
  <input type="text" ref="input" />
</template>

<script>
export default {
  mounted() {
    this.$refs.input.focus();
  },
};
</script>

<style></style>

refs are used to dynamically change/update the elements ,if the ref is used on
element then that vue is used and if ref is created on child component hen that
ref will be the comp instance
