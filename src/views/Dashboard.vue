<template>
  <div class="dashboard">
    <h1>Dashboard Page</h1>
    <div class="blah">
      {{user}}
    </div>
  </div>


</template>

<script>

  const axios = require("axios");

  export default {
    name: "Dashboard",
    data() {
      return {
        user: ""
      }
    },
    mounted() {
      axios.get("/api/user").then(user => {
        this.user = user.data.name
      });
    }
  }
</script>

<style scoped>

</style>