<template>
  <div>
  <v-layout >

    <v-flex xs6>
      <song-meta-data :song="song" />
    </v-flex>

    <v-flex xs6 v-if="song" class="ml-4">
      <song-youtube :youtubeId="song.youtubeId" />
    </v-flex>

  </v-layout>

  <v-layout class="mt-4">
    <v-flex xs6 v-if="song">
      <lyrics :lyrics="song.lyrics" />
    </v-flex>
    <v-flex xs6 class="ml-4" v-if="song">
      <tab :tab="song.tab" />
    </v-flex>
  </v-layout>
  </div>
</template>

<script>
  import SongsService from '@/services/SongsService'
  import Panel from '@/components/Panel'
  import SongMetaData from './SongMetaData'
  import SongYoutube from './SongYouTube'
  import Lyrics from './Lyrics'
  import Tab from './Tab'

  export default {
    data () {
      return {
        song: null
      }
    },
    async mounted () {
      const songId = this.$store.state.route.params.songId
      this.song = (await SongsService.show(songId)).data
    },
    components: {
      Panel,
      SongMetaData,
      SongYoutube,
      Lyrics,
      Tab
    }
  }
</script>

<style scoped>

</style>
