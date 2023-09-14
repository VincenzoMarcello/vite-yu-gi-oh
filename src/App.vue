<script>
// ???
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardList from "./components/Cards/CardsList.vue";

export default {
  data() {
    return {
      // ???
      apiYu: "https://db.ygoprodeck.com/api/v7",
    };
  },
  components: { AppHeader, CardList },
};
</script>

<template>
  <AppHeader />
  <CardList />
</template>

<style lang="scss">
@use "./assets/styles/general.scss";
</style>
