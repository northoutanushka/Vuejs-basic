<template>
  <div id="custom">
    <p>
      click the close button to hide the div
    </p>
    <input type="text" v-model="name" />
    <button @click="$emit('close', name)">close</button>
  </div>
</template>

<script>
export default {
  // emits: ["close"],
  //for vaildation use emit as a object and it will have the emit function with the parameter as passed during te emit
  emits: {
    close: (value) => {
      if (value) {
        return true;
      } else {
        return false;
      }
    },
  },
  data() {
    return {
      name: "",
    };
  },
};
</script>

<style>
div #custom {
  background-color: aqua;
}
</style>
