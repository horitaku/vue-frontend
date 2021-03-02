<template>
  <div>
    <form>
      <label for="username">
        Username:
      </label>
      <input v-model="username" type="text" name="username" value />
      <label for="password">
        Password:
      </label>
      <input v-model="password" type="password" name value />

      <button type="submit" name="button">
        Register
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      errors: null
    };
  },
  methods: {
    register() {
      this.$store
        .dispatch("register", {
          username: this.username,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: "dashboard" });
        })
        .catch(err => {
          console.log(err.response.data);
          this.errors = err.response.data.errors;
        });
    }
  }
};
</script>
