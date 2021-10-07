if you use it as title={{ tile }} and title ="abc" both will be considered a
string.thus if to bind any data value with the property we use data binding as
:title="title" alo title={{ title }} is not working becoz {{ title }} is used
alone but not as the value(RHS)
<template>
  <div>
    <div>
      <!-- <Datawithref />
    <DatawithReactive />
    <MethodView />
    <ComputedView />
    <WatchView /> -->
      <!-- <Parentcomp /> -->
      <CIHooks />
    </div>

    <p v-html="name"></p>

    <button @click="modal">Click to call or not call modal component</button>
    <br /><br />

    <div>
      <p v-for="(index, frnd) in friends" :key="frnd">{{ frnd }}{{ index }}</p>
      <button @click="addFriend">add friend</button>

      obj :{{ obj.currentName }}
      <button @click="obj.currentName = 'Anushka'">change the name</button>
    </div>

    <Inject />

    <div v-if="show">
      <br />
      <Modal
        :title="title"
        :frnz="friends"
        :colors="favColor"
        @closeEvent="modal"
      />
    </div>

    <Slotcomp>
      <template v-slot:links>
        <a href="#">Sign Up</a>
        <a href="#">Sign In</a>
      </template>
      <p>This is slot</p>
    </Slotcomp>
    <br />
    <Slotcomp>
      <template v-slot:default="slotprops">
        {{ slotprops.firstname }} {{ slotprops.lastname }}</template
      >
    </Slotcomp>
    <br />
    <br />
    <Slotcomp></Slotcomp>
    <br />
    <Slotcomp></Slotcomp>
    <!-- when we have one comp calling only then we may not named it but if we have many comp call with no content then it is adviced to use named slots -->

    <TeleportView />

    <br /><br />
    <div>
      <br />
      <input type="text" ref="age" />
      <button @click="handleClick">click to type</button>
    </div>
    <br />
    <br />
    <br />
    <Forms />

    <button @click="modal">Click to show</button>
    <div v-if="show">
      <CustomEvents @close="custom" />
    </div>

    <div>
      <button @click="activateTab = 'TabA'">Tab A</button>
      <button @click="activateTab = 'TabB'">Tab B</button>

      <!-- <TabA v-if="activateTab === 'TabA'" />
    <TabB v-if="activateTab === 'TabB'" /> -->
      <!-- instead of calling the multiple comp checking the same attribute use comp tag  -- it see for the possible value of activeTab and see its 
    corresp comp-->
      <!-- now if we have 3 tabs tht are dynamically renders then on switch to nect tab will have that comp active that time thus the data is lost of other tabs if had any thus to keep the comp alive
    wrap the comp with<keep-alive tag> this will cached the copm state -->

      <keep-alive>
        <component :is="activateTab" />
      </keep-alive>
    </div>

    <div>
      <counterclick />
      <counterhover />
    </div>

    <div>
      <p v-if="num === 0">Number is 0</p>
      <p v-else-if="num < 0">Number is negative</p>
      <p v-else-if="num > 0">Number is positive</p>
      <p v-else>it is not number</p>

      <p>{{ num }}</p>
      <button @click="num++">+</button>
      <button @click="num--">-</button>
    </div>

    <Ref />

    <div>
      <p>fullName:{{ fullName }}</p>
    </div>

    <parent /><br />
    <button @click="changeFullName()">Change name</button>
  </div>
</template>

<script>
// components are object here because they were exported as object
import Modal from "./components/Modal.vue";
import Slotcomp from "./components/Slots.vue";
import TeleportView from "./components/Teleport.vue";
import Forms from "./components/Forms.vue";
import Inject from "./components/provideAndInject.vue";
import CustomEvents from "./components/customEvent.vue";
import TabA from "./components/dynamicComponen/TabA.vue";
import TabB from "./components/dynamicComponen/TabB.vue";
import Parent from "./components/Hooks/parent.vue";
import Ref from "./components/refs.vue";
import counterclick from "../src/components/Mixin/onClick.vue";
import counterhover from "../src/components/Mixin/onHover.vue";
import Datawithref from "../src/components/composition API/datawithref.vue";
import DatawithReactive from "../src/components/composition API/dataWithReactive.vue";
import MethodView from "../src/components/composition API/methods.vue";
import ComputedView from "../src/components/composition API/computed.vue";
import WatchView from "../src/components/composition API/Watch.vue";
import Parentcomp from "../src/components/composition API/ProvideAndInject/Parent.vue";
import CIHooks from "../src/components/composition API/Hooks.vue";

export default {
  name: "App",
  components: {
    Modal,
    Slotcomp,
    TeleportView,
    Forms,
    Inject,
    CustomEvents,
    TabA,
    TabB,
    Parent,
    Ref,
    counterclick,
    counterhover,
    Datawithref,
    DatawithReactive,
    MethodView,
    ComputedView,
    WatchView,
    Parentcomp,
    CIHooks,
  },
  data() {
    return {
      activateTab: "TabA",
      name: "<b>Anushka</b>",
      firstName: "Anushka",
      lastName: "Mishra",
      title: "Click to close the modal",
      friends: ["abc", "xyz"],
      favColor: ["red", "orange"],
      obj: {
        currentName: "ani",
        age: 24,
      },
      show: false,
      num: 0,
    };
  },
  methods: {
    handleClick() {
      this.$refs.age.focus();
    },
    modal() {
      this.show = !this.show;
    },
    changeFullName() {
      // fullname is a computed property and that we can change and as the property is changed the computed property is recalculated and set function is called
      //which take the updated value
      this.fullName = "Ani Mishra";
    },
    addFriend() {
      this.friends.push("Ani");
    },
    custom(name) {
      //automatically has the argument passed
      this.modal();
      console.log(name);
    },
  },
  computed: {
    fullName: {
      get() {
        return `${this.firstName} ${this.lastName}`;
      },
      set(value) {
        const name = value.split(" ");
        this.firstName = name[0];
        this.lastName = name[1];
      },
    },
  },
  watch: {
    //watch is used to watch a vlue or computed property and take the action
    // num(newValue) {
    //   if (newValue > 5) {
    //     alert("limit reached!!!");
    //   }
    // },
    num: {
      //use the immediate property to take the action as soon as page loads
      handler(newValue) {
        if (newValue > 5) {
          alert("limit reached!!!");
        }
      },
      immediate: true,
    },
    friends: {
      //use deep watchere for array and objects
      handler(newvalue) {
        console.log(newvalue);
      },
      deep: true,
    },
    obj: {
      handler(name) {
        console.log(name);
      },
      deep: true,
    },
  },
  provide: {
    //we can use this provide to pass the variable from one component to its n level of child
    //we can pass with props but then to get it reached to n level passing from each comp will be needed thus with provide u just need to use inject
    // it is used as static data but when u want to pass it from data property this keyword will give error at that time use provide as a function
    //provide(){return {}}
    user: "Anushka Ani",
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
p {
  font-weight: normal;
  font-style: normal;
}
</style>
