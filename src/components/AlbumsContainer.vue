<template>
  <div>
    <Loading
    v-if="albumsList.length === 0"
    />

    <div class="select-container">
      <select v-model="selectedGenre" @change="filteredAlbumsList(selectedGenre)">
        <option value="">Tutti i generi</option>
        <option
        v-for="genre, i in genreList"
        :key="i"
        :value="genre">{{genre}}
        </option>
      </select>
    </div>

    <div class="container">
      <Album
      v-for="album, i in albumsList"
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
  components: {
    Album,
    Loading
  },
  data() {
    return {
      albumsList: [],
      selectedGenre: ""
    }
  },
  computed: {
    genreList() {
      let newList = [];
      this.albumsList.forEach(album => {
        if(!newList.includes(album.genre)) {
          newList.push(album.genre)
        }
      });
      // ritorno un array con la lista dei generi senza ripetizioni
      return newList;
    },
    filteredAlbumsList(selectedItem) {
      if(selectedItem === "") {
        return this.albumsList;
      } else {
        let newList = [];
        this.albumsList.forEach(album => {
          if(album.genre === selectedItem) {
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
      })
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
    justify-content: space-between;
}

.select-container {
  display: flex;
  justify-content: center;
}

</style>
