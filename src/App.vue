<script>
// ???
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardList from "./components/Cards/CardsList.vue";
import BaseSelect from "./components/Select/BaseSelect.vue";

export default {
  data() {
    return {
      // ???
      apiYu: "https://db.ygoprodeck.com/api/v7",
    };
  },
  components: { AppHeader, CardList, BaseSelect },

  methods: {
    search(selectedType) {
      const fullApiYu = `${this.apiYu}/cardinfo.php?archetype=${selectedType}`;
      console.log(fullApiYu);
    },

    // ???
    fetchArch(fullApiYu) {
      axios.get(fullApiYu).then((response) => {
        this.archetypes = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>

<template>
  <AppHeader />
  <BaseSelect @archtype-serch="search" />
  <CardList />
</template>

<style lang="scss">
@use "./assets/styles/general.scss";
</style>
