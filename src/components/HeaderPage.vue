<template>
  <header class="header">
    <div class="logo">
      <h1>BOOLFLIX</h1>
    </div>
    <label for="search">
      <input type="text" placeholder="Cerca il tuo fil preferito...">
      <button>Cerca</button>
    </label>
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
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
