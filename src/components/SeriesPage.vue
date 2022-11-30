<template>
  <div>
    <h2>Serie TV</h2>
    <div class="container">
      <CardPage
      v-for="serie in arrSeries"
      :key="serie.id"
      :imgUrl="`${imgPrefix}${serie.poster_path}`"
      :title1="serie.title"
      :title2="serie.original_title"
      :language="serie.original_language"
      :rating="serie.vote_average"
      :overview="serie.overview"/>
    </div>
  </div>
</template>

<script>
import CardPage from '@/components/CardPage.vue';

export default {
  name: 'SeriesPage',
  components: {
    CardPage,
  },

  props: {
    arrSeries: Array,
  },

  data() {
    return {
      imgPrefix: 'https://image.tmdb.org/t/p/original',
    };
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
