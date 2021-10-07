<template>
  <div>
    <p>technology name is {{ profile.name }}</p>
    <p>technology version is {{ profile.version }}</p>
    <p>technology updated version is {{ profile.updated }}</p>
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  setup() {
    const profile = reactive({
      name: "vue",
      version: 2,
      updated: 3,
    });
    const welcome = `welcome to ${profile.name} having version ${profile.version}`;
    // in return if we return one by one property then change in the values is not known to it and suppose settimeout is written to update the properties in 2 sec
    // and if return it one by one as name,,, then this will not be updated
    //for me this return is working but in some cases u may need to write as return toRefs(profile)
    //https://stackoverflow.com/questions/66585688/what-is-the-difference-between-ref-toref-and-torefs
    //as to refs bind it to the template u need not use profile.name instead directly use as name
    return {
      profile,
      welcome,
    };
  },
};
</script>

<style></style>
