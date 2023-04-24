<template>
  <div>
    <button @click="gamble">gamble</button>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";
export default {
  data() {
    return {
      wins: cookies.get(`wins`),
      losses: cookies.get(`losses`),
    };
  },
  methods: {
    gamble() {
      axios
        .request({
          url: `http://www.randomnumberapi.com/api/v1.0/randomnumber`,
        })
        .then((response) => {
          let number = response.data[0];
          if (number > 50) {
            let newwin = JSON.parse(this.wins) + 1;
            cookies.set(`wins`, newwin);
            this.$root.$emit(`wins`, this.wins);
          } else {
            let newloss = JSON.parse(this.losses) + 1;
            cookies.set(`losses`, newloss);
            this.$root.$emit(`losses`, this.losses);
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