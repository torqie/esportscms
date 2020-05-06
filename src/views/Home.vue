<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <form action="" @submit.prevent="login">
      <input type="email" name="email" id="email" v-model="email">
      <input type="password" name="password" id="password" v-model="password">
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>

const axios = require("axios");
axios.defaults.withCredentials = true;
axios.defaults.baseURL = "http://localhost:8000"
export default {
  name: 'Home',

  data() {
    return {
      email: "",
      password: "",
    }
  },

  methods: {
    login() {
      axios.get("/sanctum/csrf-cookie").then(response => {
        axios.post("/login", {
          email: this.email,
          password: this.password,
        }).then(res => {
          console.log("User: ", res);
          
          this.$router.push({ name: "Dashboard" });
        });
      });
    }
  }
}
</script>
