<script>
import axios from "axios";

export default {
  data() {
    return {
      cards: [],
    };
  },

  methods: {
    fetchCards() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((response) => {
          console.log(response.data.data);
        });
    },
  },

  created() {
    this.fetchCards();
  },
};
</script>

<template></template>

<style></style>
