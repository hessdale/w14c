<template>
  <div>
    <page-header></page-header>
    <section>
      <game-button></game-button>
      <score-board></score-board>
    </section>
  </div>
</template>

<script>
import ScoreBoard from "@/components/ScoreBoard.vue";
import GameButton from "@/components/GameButton.vue";
import PageHeader from "@/components/PageHeader.vue";
import cookies from "vue-cookies";

export default {
  components: {
    PageHeader,
    GameButton,
    ScoreBoard,
  },
  mounted() {
    if (cookies.get(`login_token`) != null) {
      document
        .querySelector(`section`)
        .insertAdjacentHTML(`beforeend`, `<h1>welcome</h1>`);
    } else {
      this.$router.push(`/`);
    }
  },
};
</script>

<style scoped>
</style>