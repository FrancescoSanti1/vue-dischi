<template>
  <div id="app">
    <Header
      :list="arrayToPass"
      @filter="passGenreToChild"
    />
    <main>
      <AlbumsContainer
        :changedGenre="genreToPass"
        @axiosIsDone="passArrayToChild"
      />
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
  },
  data() {
    return {
      // tramite le props, ogni volta che questi dati vengono aggiornati, vengono inviati al figlio
      arrayToPass: [],
      genreToPass: ""
    }
  },
  methods: {
    passArrayToChild(arrayName) {
      // l'evento custom axiosIsDone invoca questa funzione che aggiorna l'array coi generi
      this.arrayToPass = arrayName;
    },
    passGenreToChild(genreName) {
      // l'evento custom filter invoca questa funzione che aggiorna il valore del genere selezionato
      this.genreToPass = genreName;
    }
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
  min-height: calc(100vh - 70px);
  padding: 50px 0;
}
</style>
