<template>
  <header class="header">
    <div class="logo">
      <h1>BOOLFLIX</h1>
    </div>
    <label for="search">
      <input
      v-model="query"
      type="text"
      placeholder="Cerca il tuo fil preferito..."
      @keyup.enter="$emit()"
      >
      <button>Cerca</button>
    </label>
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
