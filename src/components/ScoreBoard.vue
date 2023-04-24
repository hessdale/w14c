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
    update_wins() {
      this.wins = cookies.get(`wins`);
    },
    update_loss() {
      this.loss = cookies.get(`losses`);
    },
  },
  data() {
    return {
      wins: undefined,
      loss: undefined,
    };
  },

  mounted() {
    if (cookies.get(`wins`) == null) {
      cookies.set(`wins`, 0);
      this.wins = 0;
    }
    if (cookies.get(`losses`) == null) {
      cookies.set(`losses`, 0);
    }
    this.$root.$on(`wins`, this.update_wins);
    this.$root.$on(`wins`, this.update_loss);
  },
};
</script>

<style scoped>
</style>