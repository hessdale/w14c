<template>
  <div>
    <page-header></page-header>
    <section>
      <label for="user">user:</label>
      <input type="text" name="user" ref="username" />
      <label for="pass">pass:</label>
      <input type="text" name="pass" ref="password" />
    </section>
    <button @click="check_login">Log in</button>
    <p>eve.holt@reqres.in</p>
    <p>cityslicka</p>
    <div ref="error_message"></div>
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader.vue";
import cookies from "vue-cookies";
import axios from "axios";
export default {
  components: {
    PageHeader,
  },
  methods: {
    check_login() {
      let user_value = this.$refs.username[`value`];
      let pass_value = this.$refs.password[`value`];
      cookies;
      axios
        .request({
          url: `https://reqres.in/api/login`,
          method: `POST`,
          data: {
            email: user_value,
            password: pass_value,
          },
        })
        .then((response) => {
          response;
          this.$router.push(`/game`);
          cookies.set(`login_token`, `${response.data.token}`);
        })
        .catch((error) => {
          error;
          this.$refs.error_message.insertAdjacentHTML(
            `beforeend`,
            `<h1>try again</h1>`
          );
        });
    },
  },
};
</script>

<style scoped>
</style>