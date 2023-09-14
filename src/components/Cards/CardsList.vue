<script>
import axios from "axios";
import Card from "./Card.vue";
import BaseSelect from "../Select/BaseSelect.vue";

export default {
  data() {
    return {
      cards: [],
      apiYu: "https://db.ygoprodeck.com/api/v7",
    };
  },

  components: { Card, BaseSelect },

  methods: {
    fetchCards() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((response) => {
          this.cards = response.data.data;
          console.log(response.data.data);
        });
    },

    search(selectedType) {
      const fullApiYu = `${this.apiYu}/cardinfo.php?archetype=${selectedType}`;

      axios.get(fullApiYu).then((response) => {
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
    <BaseSelect @archtype-serch="search" />

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
