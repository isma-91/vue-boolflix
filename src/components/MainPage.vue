<template>
  <div>
    <FilmsPage />
    <SeriesPage />
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
};
</script>

<style lang="scss" scoped>

</style>
