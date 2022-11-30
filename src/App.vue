<template>
  <div>
    <HeaderPage />
    <MainPage />
  </div>
</template>

<script>
// import axios from 'axios';
import HeaderPage from '@/components/HeaderPage.vue';
import MainPage from '@/components/MainPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },

};
</script>

<style lang="scss">

</style>
