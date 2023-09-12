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
          this.cards = response.data.data;
          console.log(response.data.data);
        });
    },
  },

  created() {
    this.fetchCards();
  },
};
</script>

<template>
  <div class="container">
    <div class="row g-4 row-cols-2 row-cols-md-3 row-cols-lg-5 my-5">
      <div class="col" v-for="card in cards" :key="card.id">
        <img v-for="image of card.card_images" :src="image.image_url" alt="" />
        <p>{{ card.name }}</p>
        <p>{{ card.type }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
img {
  max-width: 100%;
}
p {
  text-align: center;
  font-weight: 500;
  font-size: 0.8rem;

  margin-top: 5px;
  margin-bottom: 0;
  padding: 1rem;

  border: 1px solid black;
  border-radius: 5px;

  background-color: antiquewhite;
  cursor: pointer;
}
</style>
