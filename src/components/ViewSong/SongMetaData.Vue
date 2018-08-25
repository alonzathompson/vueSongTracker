<template>
      <panel title="Song">
        <v-layout v-if="song">
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
                  name: 'song-edit',
                  params: {
                    songId: song.id
                  }
                }">
                Edit Song
              </v-btn>
            </v-flex>

            <v-flex xs6>
              <img class="album-image"
                :src="song.albumImageUrl" />
              <br />
              {{song.album}}
            </v-flex>
        </v-layout>
      </panel>
</template>

<script>
  import Panel from '@/components/Panel'
  export default {
    props: [
      'song'
    ],
    components: {
      Panel
    }
  }
</script>

<style scoped>
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
