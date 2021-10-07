<template>
  <div>
    <form action="" class="form">
      <label for="Email">Email:</label>
      <input
        type="text"
        placeholder="Type your email address here"
        v-model="email"
      />
      <br />
      <label for="Password:">Password: </label>
      <input
        type="text"
        placeholder="Type your password here"
        v-model="password"
      />
      <br /><br />
      <label for="role">Role:</label>
      <select v-model="role">
        <option value="Web designer">Web designer</option>
        <option value="Web Developer">Web Developer</option>
      </select>
      <br />
      Add your skills:
      <input type="text" name="" id="" @keyup.alt="add" v-model="skill" />
      <br />
      <button id="skills" v-for="skill in skillsarray" :key="skill">
        <span @click="deleteskills(skill)">{{ skill }}</span>
      </button>

      <div>
        <input type="checkbox" name="accept" id="accept" />
        <p class="check">
          please mark the checkbox to accept the terms and conditions
        </p>
      </div>
    </form>
    <p>email address is :{{ email }}</p>
    <p>password is:{{ password }}</p>
    <p>role is :{{ role }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "Web Developer",
      skill: "",
      skillsarray: [],
    };
  },
  methods: {
    add(e) {
      if (e.key === "," && this.skill) {
        if (!this.skillsarray.includes(this.skill)) {
          this.skillsarray.push(this.skill);
        }
        this.skill = "";
      }
    },
    deleteskills(skill) {
      this.skillsarray = this.skillsarray.filter((item) => {
        return skill !== item;
      });
    },
  },
};
</script>

<style>
label {
  margin-right: 0%;
}
.form {
  width: 700px;
  height: 250px;
  background-color: aqua;
  margin: auto;
  text-align: left;
}
input {
  margin-top: 20px;
  width: 50%;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
}
.check {
  display: inline-block;
}
#skills {
  display: inline-block;
  padding: 5px;
  background-color: rgb(235, 224, 224);
  border-style: none;
  margin-right: 5px;
}
</style>
