<template>
  <div id="nav">
    <router-link to="/">
      Home
    </router-link>
    <router-link v-if="loggedIn" to="/dashboard">
      Dashboard
    </router-link>
    <router-link v-if="!loggedIn" to="/login" class="button">
      Login
    </router-link>
    <button v-else type="button" class="logoutButton" @click="logout">
      Logout
    </button>
  </div>
</template>

<script>
import { authComputed } from "../store/helpers";

export default {
  computed: {
    ...authComputed
  },
  methods: {
    logout() {
      console.log("Logged out");
      this.$store.dispatch("logout");
    }
  }
};
</script>

<style scoped></style>
