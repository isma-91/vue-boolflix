<template>
  <div class="card">
      <img :src="imgUrl" :alt="title2">
    <ul class="infos">
      <li class="title">
        TITOLO: <span>{{ title1 }}</span>
      </li>
      <li class="original-title">
        Titolo Originale: <span>{{title2}}</span>
      </li>
      <li class="language">
        Lingua: <span>{{ language }}</span>
      </li>

      <li class="rating">
        Voto: <span>{{ rating }}</span>
        <div class="outer-stars-container">
          <div class="outer-stars" v-for="num in 5" :key="num">
            <font-awesome-icon icon="fa-regular fa-star"/>
          </div>
          <div class="inner-stars-container">
            <div class="inner-stars" v-for="i in realRating" :key="i">
              <font-awesome-icon icon="fa-solid fa-star-of-life"/>
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
  data() {
    return {
      realRating: Math.floor(this.rating / 2),
      // eslint-disable-next-line
      // Usare il math floor perche altrimenti i valori con la virgola rompono tutto e non fa visualizzare tuttt i film/telefim
    };
  },
  created() {
    console.log(this.realRating);
  },
};
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  border: 2px solid white;
  width: calc((100% - 1rem * 2) / 3);
  overflow: hidden;
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
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
    top: 0px;
    left: 0px;
    transform: translateX(-100%);
    z-index: 1;

    li{
      margin: .7rem 0;
    }
    span {
    font-weight: 400;
    font-size: 20px;
    color: lightgray;
    };
  }
}

.card:hover {
  cursor: pointer;
}
.card:hover img{
opacity: 0.2;
}

.card:hover .infos {
  transition: all 0.5s ease;
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
