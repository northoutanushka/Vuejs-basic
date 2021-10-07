<template>
  <div>
    <slot>default slots</slot>
    <slot name="links"></slot>
    <slot :firstname="firstname" :lastname="lastname"></slot>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstname: "firstname",
      lastname: "lastname",
    };
  },
};
</script>
