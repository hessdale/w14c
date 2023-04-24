<template>
  <div>
    <button @click="gamble">gamble</button>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";
export default {
  methods: {
    gamble() {
      axios
        .request({
          url: `http://www.randomnumberapi.com/api/v1.0/randomnumber`,
        })
        .then((response) => {
          let number = response.data[0];
          if (number > 50) {
            let wins = cookies.get(`wins`);
            let newwin = JSON.parse(wins) + 1;
            cookies.set(`wins`, newwin);
            this.$root.$emit(`wins`, newwin);
          } else {
            let losses = cookies.get(`losses`);
            let newloss = JSON.parse(losses) + 1;
            cookies.set(`losses`, newloss);
            this.$root.$emit(`losses`, newloss);
          }
        })
        .catch((error) => {
          error;
        });
    },
  },
};
</script>

<style scoped>
</style>