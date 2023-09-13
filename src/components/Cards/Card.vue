<script>
export default {
  props: {
    image_url: String,
    name: String,
    type: String,
  },
};
</script>

<template>
  <div class="col">
    <img :src="image_url" alt="" />
    <p>{{ name }}</p>
    <p>{{ type }}</p>
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

  background-color: rgba(250, 235, 215, 0.9);
  cursor: pointer;
}
</style>
