<template>
  <v-layout column>
    <v-flex >
      <songs-search-panel />
      <song-panel />
    </v-flex>
  </v-layout>
</template>

<script>
  import Panel from '@/components/Panel'
  import SongsSearchPanel from './SongsSearchPanel'
  import SongPanel from './SongPanel'
  import SongsService from '@/services/SongsService'
  export default {
    components: {
      Panel,
      SongPanel,
      SongsSearchPanel
    },
    data () {
      return {
        songs: null
      }
    },
    async mounted () {
      this.songs = (await SongsService.index()).data
    }
  }
</script>

<style scoped>
  .song{
    padding: 20px;
    height: 330px;
    overflow: hidden;
  }
  .song-title{
    font-size: 30px;
  }
  .song-artist{
    font-size: 24px;
  }
  .album-image {
    margin: 0 auto;
    width: 70%;
  }
</style>
