<script>
import {
  onBeforeMount,
  onBeforeUnmount,
  onBeforeUpdate,
  onMounted,
  onUnmounted,
  onUpdated,
} from "@vue/runtime-core";
export default {
  //just on is addef before the name as compared to options api and a callback function is called on each methods
  // onbeforecreated and oncreated are not need as this are replaced with setup function
  setup() {
    onBeforeMount(() => {
      console.log(" CI before mounting");
    });
    onMounted(() => {
      console.log(" CI mounted");
    });
    onBeforeUpdate(() => {
      console.log("CI before updates");
    });
    onUpdated(() => {
      console.log("CI updated");
    });
    onBeforeUnmount(() => {
      console.log("CI before unmount");
    });
    onUnmounted(() => {
      console.log("CI unmounted");
    });
  },
};
</script>

<style></style>
