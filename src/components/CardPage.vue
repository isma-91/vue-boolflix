<template>
  <div class="card">
    <div class="video-img">
      <img :src="imgUrl" :alt="title2">
    </div>
    <div class="infos">
      <h3 class="title">{{ title1 }}</h3>
      <h3 class="original-title">{{title2}}</h3>
      <div class="lenguage">{{ lenguage }}</div>
      <div class="rating">{{ rating }}</div>
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
    lenguage: String,
    rating: Number,
  },
};
</script>

<style lang="scss" scoped>

</style>
