<template>
  <header class="header">
    <div class="logo">
      <h1>BOOLFLIX</h1>
    </div>
    <form @submit.prevent="$emit('search', query)">
      <label  for="search">
        <input
        v-model="query"
        type="text"
        placeholder="Cerca il tuo fil preferito..."
        >
      </label>
      <button>Cerca</button>
    </form>
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
  data() {
    return {
      query: '',
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 100px;
  background-color: black;
    h1 {
      color: red;
    }
}
</style>
