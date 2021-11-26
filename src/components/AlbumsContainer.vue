<template>
  <div>
    <Loading
    v-if="AlbumsList.length === 0"
    />
    <div class="container">
      <Album
      v-for="album, i in AlbumsList"
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
      AlbumsList: []
    }
  },
  // computed() {
  //   return {
  //     listLength() {
  //       return this.AlbumsList.length
  //     }
  //   }
  // },
  created() {
    // il timeout è a scopo didattico per vedere il Loading comparire
    setTimeout(this.getAlbums, 3000);
    console.log(this.AlbumsList);
  },
  methods: {
    getAlbums: function() {
      axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.AlbumsList = result.data.response;
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

</style>
