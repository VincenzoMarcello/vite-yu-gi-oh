<script>
import AppHeader from "./components/AppHeader.vue";
import CardList from "./components/Cards/CardsList.vue";

export default {
  components: { AppHeader, CardList },

  methods: {},
};
</script>

<template>
  <AppHeader />
  <CardList />
</template>

<style lang="scss">
@use "./assets/styles/general.scss";
</style>
