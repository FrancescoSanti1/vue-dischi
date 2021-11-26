<template>
  <header>
      <img src="../assets/img/logo-small.svg" alt="logo Spotify">
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header {
    background-color: #2e3a46;
    height: 70px;
    line-height: 70px;
    padding: 0 20px;

    img {
        height: 40px;
        vertical-align: middle;
    }
}
</style>
