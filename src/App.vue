<template>
  <div id="app">
    <Header/>
    <main>
      <AlbumsContainer/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import AlbumsContainer from './components/AlbumsContainer.vue'

export default {
  name: 'App',
  components: {
    Header,
    AlbumsContainer,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

main {
  background-color: #1e2d3b;
  padding: 50px 0;
}
</style>
