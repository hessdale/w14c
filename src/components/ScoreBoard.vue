<template>
  <div>
    <h1>Wins: {{ wins }}</h1>
    <h1>Losses: {{ loss }}</h1>
  </div>
</template>

<script>
import cookies from "vue-cookies";
export default {
  methods: {
    //functions that get cookies to update the wins and losses variable
    update_wins() {
      this.wins = cookies.get(`wins`);
    },
    update_loss() {
      this.loss = cookies.get(`losses`);
    },
  },
  data() {
    return {
      wins: cookies.get(`wins`),
      loss: cookies.get(`losses`),
    };
  },

  mounted() {
    //sets wins to 0 and sets cookie if cookies are undefined
    if (cookies.get(`wins`) == null) {
      cookies.set(`wins`, 0);
      this.wins = 0;
    }
    if (cookies.get(`losses`) == null) {
      cookies.set(`losses`, 0);
      this.loss = 0;
    }
    //listening for data from game button
    this.$root.$on(`wins`, this.update_wins);
    this.$root.$on(`losses`, this.update_loss);
  },
};
</script>

<style scoped>
</style>