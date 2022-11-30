<template>
  <div class="card">
      <img :src="imgUrl" :alt="title2">
    <div class="infos">
      <h3 class="title">{{ title1 }}</h3>
      <h3 class="original-title">{{title2}}</h3>
      <div class="language">{{ language }}</div>
      <div class="rating">{{ rating }}</div>
      <div class="overview">{{ overview }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardPage',
  props: {
    imgUrl: String,
    title1: String,
    title2: String,
    language: String,
    rating: Number,
    overview: String,
  },
};
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  border: 2px solid red;
  width: calc((100% - 1rem * 2) / 3);
  overflow-y:auto;
  img {
    width: 100%;
    object-fit: contain;
  }
  .infos {
    position: absolute;
    top: 20px;
    left: 20px;
    display: none;
  }
}
</style>
