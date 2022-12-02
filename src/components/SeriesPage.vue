<template>
  <div v-if="arrSeries">
    <h2>Serie TV</h2>
    <div class="container">
      <CardPage
      v-for="serie in arrSeries"
      :key="serie.id"
      :imgUrl="getImage(serie.poster_path)"
      :title1="serie.name"
      :title2="serie.original_name"
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
  methods: {
    getImage(path) {
      if (path) {
        return this.imgPrefix + path;
      }
      return null;
    },
  },
};
</script>

<style lang="scss" scoped>

h2 {
  font-size: 50px;
  color: white;
}
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-top: 1rem;
}
</style>
