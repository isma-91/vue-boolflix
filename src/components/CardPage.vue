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
};
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  border: 2px solid red;
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
</style>
