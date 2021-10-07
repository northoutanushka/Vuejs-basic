<template>
  <div class="div" @click.self="close">
    <div id="modal" :class="{ apply: colors.includes('red') }">
      <p>{{ title }}</p>
      <p>{{ frnz[0] }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "frnz", "colors"],
  methods: {
    close() {
      this.$emit("closeEvent");
    },
  },
};
</script>

<style>
#modal p {
  font-weight: bold;
  font-style: italic;
}
.apply {
  color: red;
  background-color: rgb(221, 196, 196);
}
.div {
  width: 500px;
  height: 300px;
  background-color: aqua;
  margin-left: 100px;
}
</style>

or style scoped p{ font-weight: bold; font-style: italic; } /style --events now
as we are calling the modal comp from app and that has method to show the comp
and hide but if we want to call that show hide method of parent comp from the
child comp then define and call the method which emits the custom event which
then is listen by your parent comp from where the chid is called and then call
the desired method now the events has modifiers - i have used self here means
fire the event only when that element is clicked as if the parent has some click
event then all the child will also have the access to it thus to avoid it we use
self
