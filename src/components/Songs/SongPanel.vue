<template>
  <panel title="Songs">
      <v-btn
        slot="action"
        class="cyan accent-3"
        :to="{
          name: 'song-create'
        }"
        light
        small
        absolute
        flat
        right
        middle
        raised>
        <v-icon>add</v-icon>
      </v-btn>
    <div
      v-for="song in songs"
      class="song"
      :key="song.id">

      <v-layout>

        <v-flex xs6>
          <div class="song-title">
            {{song.title}}
          </div>
          <div class="song-artist">
            {{song.artist}}
          </div>
          <div class="song-album">
            {{song.album}}
          </div>
          <div class="song-album">
            {{song.genre}}
          </div>
          <v-btn
            class="cyan"
            dark
            :to="{
              name: 'song',
              params: {
                songId: song.id
              }
            }">
            View
          </v-btn>
        </v-flex>

        <v-flex xs6>
          <img class="album-image"
            :src="song.albumImageUrl" />
          <br />
          {{song.album}}
        </v-flex>

      </v-layout>

    </div>
  </panel>
</template>

<script>
  import SongsService from '@/services/SongsService'
  import Panel from '@/components/Panel'

  export default {
    components: {
      Panel
    },
    data () {
      return {
        songs: null
      }
    },
    watch: {
      '$route.query.search': {
        immediate: true,
        async handler (value) {
          this.songs = (await SongsService.index(value)).data
        }
      }
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
