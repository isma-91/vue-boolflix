<template>
  <div v-if="arrFilms">
    <h2>Film</h2>
    <div class="container">
      <CardPage
    v-for="film in arrFilms"
    :key="film.id"
    :imgUrl="getImage(film.poster_path)"
    :title1="film.title"
    :title2="film.original_title"
    :language="film.original_language"
    :rating="film.vote_average"
    :overview="film.overview"
    />
    </div>
  </div>
</template>

<script>
import CardPage from '@/components/CardPage.vue';

export default {
  name: 'FilmsPage',
  components: {
    CardPage,
  },
  props: {
    arrFilms: Array,
  },

  data() {
    return {
      imgPrefix: 'https://image.tmdb.org/t/p/w342',
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
  margin-bottom: 3rem;
}
</style>
