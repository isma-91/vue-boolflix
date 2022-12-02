<template>
  <div class="card">
      <img v-if="imgUrl"
      :src="imgUrl" :alt="title2">
      <img v-else
      src="@/assets/img/default-img.png" :alt="title2">
    <ul class="infos">
      <li class="title">
        TITOLO: <span>{{ title1 }}</span>
      </li>
      <li class="original-title">
        Titolo Originale: <span>{{title2}}</span>
      </li>
      <li class="language">
        <!-- Lingua: <span>{{ language }}</span> -->
        Lingua: <lang-flag :iso="language" />
      </li>

      <li class="rating">
        <!-- Voto: <span>{{ rating }}</span> -->
        Voto:
        <div class="outer-stars-container">
          <div class="outer-stars" v-for="num in 5" :key="num">
            <font-awesome-icon icon="fa-regular fa-star" class="star"/>
          </div>
          <div class="inner-stars-container">
            <div class="inner-stars" v-for="i in realRating" :key="i">
              <font-awesome-icon icon="fa-solid fa-star" class="star"/>
            </div>
          </div>
        </div>
      </li>

      <li class="overview">
        Overview: <span>{{ overview }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

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
  components: {
    LangFlag,
  },
  data() {
    return {
      realRating: Math.ceil(this.rating / 2),
      // eslint-disable-next-line
      // Usare il math floor perche altrimenti i valori con la virgola rompono tutto e non fa visualizzare tuttt i film/telefim
    };
  },
  // methods: {
  //   getFlags() {
  //     this.language.replace('it');
  //   },
  // },
  created() {
    console.log(this.realRating);
  },
};
</script>

<style lang="scss" scoped>
.card {
  border-radius: 30px;
  position: relative;
  width: calc((100% - 1rem * 2) / 3);
  overflow: hidden;
  box-shadow: 0 0 8px white;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  .infos {
    height: 100%;
    color: white;
    background-color: black;
    font-size: 25px;
    font-weight: bold;
    width: 100%;
    padding: 1rem;
    position: absolute;
    overflow-y: auto;
    -ms-overflow-style: none;  /* Hide Scrollbar IE and Edge */
    scrollbar-width: none; /* Hide Scrollbar Firefox */

    top: 0px;
    left: 0px;
    transform: translateX(-100%);
    opacity: 0;
    z-index: 1;

    li{
      margin: .7rem 0;
    }
    span {
    font-weight: 400;
    font-size: 20px;
    color: lightgray;
    margin-left: 5px;
    };

    .flag-icon{
      font-size: 25px;
    }
    .rating {
      display: flex;
    }

    .outer-stars-container{
      margin-left: 1rem;
      color: yellow;
    }
  }
}

/* Hide scrollbar Chrome, Safari and Opera */
.infos::-webkit-scrollbar {
    display: none;
}

.card:hover {
  cursor: pointer;
}
.card:hover img{
opacity: 0.2;
}

.card:hover .infos {
  transition: all 0.5s ease;
  opacity: 1;
  transform: translateX(0);
}

.outer-stars-container {
  display: flex;
position: relative;
}
.inner-stars-container {
  display: flex;
  flex-wrap: nowrap;
  flex: 0 0 0;
  position: absolute;
  overflow: hidden;
  top: 0;
  left: 0;
  width: 100%;

// eslint-disable-next-line (non funge)
// volevo provare il metodo della width, per fare apparire le stelline,
//trasformando il rating in percentuale con la quale alungare
//o accorciare il contenitore delle stelline piene così da farle apparire
//a seconda della width del genitore guidata dal rating... come fare?

}
</style>
