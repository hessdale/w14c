<template>
  <div>
    <page-header></page-header>
    <div v-if="login_cookie != undefined">
      <h3>Welcome user</h3>
      <button>gamble</button>
    </div>
    <div v-else>
      <h5>Please log in</h5>
    </div>
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader.vue";
import cookies from "vue-cookies";
export default {
  data() {
    return {
      login_cookie: cookies.get(`token`),
    };
  },
  components: {
    PageHeader,
  },
};
</script>

<style scoped>
</style>