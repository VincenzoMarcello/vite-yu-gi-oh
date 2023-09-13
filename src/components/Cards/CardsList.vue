<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  data() {
    return {
      cards: [],
    };
  },

  components: { Card },

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
      <!-- <div class="col" v-for="card in cards" :key="card.id">
        <img :src="card.card_images[0].image_url" alt="" />
        <p>{{ card.name }}</p>
        <p>{{ card.type }}</p>
      </div> -->

      <!-- STAMPA COMPONENTE CARD CON V-FOR DEL COMPONENTE -->

      <Card
        v-for="card in cards"
        :key="card.id"
        :image_url="card.card_images[0].image_url"
        :name="card.name"
        :type="card.type"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
