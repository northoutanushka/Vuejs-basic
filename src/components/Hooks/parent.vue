<template>
  <div>
    <h2>parent component</h2>
    <!-- if child id true then parent mount k phle child will mount and id child is false parent mount k bd child created will be called-->
    <button @click="show = !show">click</button>
    <child v-if="show" />
  </div>
</template>

<script>
import child from "../Hooks/child.vue";
export default {
  components: { child },
  data() {
    return {
      show: true,
    };
  },
  beforeCreated() {
    console.log("parent before created");
  },
  created() {
    console.log("parent created");
  },
  beforeMount() {
    console.log("parent before mounted");
  },
  mounted() {
    console.log("parent mounted");
  },
  beforeUpdate() {
    console.log("parent before update");
  },
  updated() {
    console.log("parent updated");
  },
  beforeUnmount() {
    console.log("parent before unmount");
  },
  unmounted() {
    console.log("parent unmounted");
  },
};
</script>

<style></style>

activated () this is called when keep-alive component is activated deactivated()
is called when keep alive comp is deactivated errorCaptured() Called when an
error from any descendent component is captured. The hook receives three
arguments: the error, the component instance that triggered the error, and a
string containing information on where the error was captured. The hook can
return false to stop the error from propagating further. renderTrack() Called
when virtual DOM re-render is tracked. The hook receives a debugger event as an
argument. This event tells you what operation tracked the component and the
target object and key of that operation. renderTriggered() Called when virtual
DOM re-render is triggered. Similarly to renderTracked, receives a debugger
event as an argument. This event tells you what operation triggered the
re-rendering and the target object and key of that operation.
