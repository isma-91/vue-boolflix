<template>
  <div class="container">
    <FilmsPage :arrFilms="arrFilms" />
    <SeriesPage :arrSeries="arrSeries" />
  </div>
</template>

<script>
import FilmsPage from '@/components/FilmsPage.vue';
import SeriesPage from '@/components/SeriesPage.vue';

export default {
  name: 'MainPage',
  components: {
    FilmsPage,
    SeriesPage,
  },
  props: {
    arrFilms: Array,
    arrSeries: Array,
  },
};
</script>

<style lang="scss" scoped>

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 5rem 0;
}
</style>
