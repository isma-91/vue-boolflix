<template>
  <div>
    <HeaderPage @search="search"/>
    <MainPage
    :arrFilms="arrFilms"
    :arrSeries="arrSeries"
    />
  </div>
</template>

<script>
import axios from 'axios';
import HeaderPage from '@/components/HeaderPage.vue';
import MainPage from '@/components/MainPage.vue';
// import FlagIcon from 'vue-flag-icon';

// App.use(FlagIcon);
export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },

  data() {
    return {
      arrFilms: null,
      arrSeries: null,
      urlApiMovies: 'https://api.themoviedb.org/3/search/movie',
      urlApiSeries: 'https://api.themoviedb.org/3/search/tv',
      apiKey: '6cb72fac1b5f0bbea7b201c9871ac213',
      query: '',
      language: 'it-IT',
    };
  },

  methods: {
    // Ascoltando l'emit dell'header eseguiamo questa funzione per dare il valore ricevuto dall'emit
    // passato per argomento, e lo diamo alla variabile 'query'
    // che poi ci servirà per la nostra ricerca nell'API
    search(data) {
      this.query = data;
      console.log(`info catturate ${data}`);

      //  Popoliamo array dei Film
      axios.get(this.urlApiMovies, {
        params: {
          api_key: this.apiKey,
          query: this.query,
          language: this.language,
        },
      })
        .then((axiosResult) => {
        // console.log(axiosResult);
          this.arrFilms = axiosResult.data.results;
          console.log(this.arrFilms);
        });

      // Popoliamo array delle serie tv
      axios.get(this.urlApiSeries, {
        params: {
          api_key: this.apiKey,
          query: this.query,
          language: this.language,
        },
      })
        .then((axiosResult) => {
        // console.log(axiosResult);
          this.arrSeries = axiosResult.data.results;
          console.log(this.arrSeries);
        });
    },
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Asap+Condensed:wght@400;600;700&display=swap');

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  font-family: 'Asap Condensed', sans-serif;
}

body {
  background-color: rgb(27, 27, 48);
}

ul {
  list-style: none;
}
</style>
