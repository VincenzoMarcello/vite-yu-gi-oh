<script>
import axios from "axios";

export default {
  data() {
    return {
      archetypes: [],
      selectedType: "",
    };
  },

  methods: {
    fetchArch() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then((response) => {
          this.archetypes = response.data;
          console.log(response.data);
        });
    },
  },

  created() {
    this.fetchArch();
  },
};
</script>

<template>
  <div class="container d-flex align-items-center mt-5">
    <select
      v-model="selectedType"
      @change="$emit('archtype-serch', selectedType)"
      class="form-select"
      aria-label="Default select example"
    >
      <option v-for="archetype in archetypes" :value="archetype.archetype_name">
        {{ archetype.archetype_name }}
      </option>
    </select>
  </div>
</template>

<style>
.form-select {
  width: 20%;
}
</style>
