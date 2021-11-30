<template>
  <div>
    <Loading
    v-if="albumsList.length === 0"
    />

    <div class="container">
      <Album
      v-for="album, i in filteredAlbumsList"
      :key="i"
      :details="album"
      />
    </div>
  </div>
</template>

<script>
import Album from '@/components/Album.vue'
import Loading from '@/components/Loading.vue'
import axios from 'axios'

export default {
  name: 'AlbumsContainer',
  props: {
    changedGenre: String
  },
  components: {
    Album,
    Loading,
  },
  data() {
    return {
      albumsList: [],
      genresList: [],
    }
  },
  computed: {
    filteredAlbumsList() {
      if(this.changedGenre === "") {
        return this.albumsList;
      } else {
        let newList = [];
        this.albumsList.forEach(album => {
          if(album.genre === this.changedGenre) {
            newList.push(album);
          }
        });
        // ritorno un array di oggetti con la lista degli album che fanno parte del genere selezionato
        return newList;
      }
    }
  },
  created() {
    // il timeout è a scopo didattico per vedere il Loading comparire
    setTimeout(this.getAlbums, 1000);
    console.log(this.albumsList);
  },
  methods: {
    getAlbums: function() {
      axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.albumsList = result.data.response;

        // una volta ottenuti i dati, creo l'array con i generi, senza ripetere eventuali ripetizioni
        this.albumsList.forEach(album => {
          if(!this.genresList.includes(album.genre)) {
            this.genresList.push(album.genre)
          }
        });
      });

      // una volta creato anche l'array, passo la lista dei generi al padre (App.vue) con l'evento custom
      this.$emit('axiosIsDone', this.genresList);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.container {
    width: 70%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
}

</style>
