<template>
  <v-layout>
    <v-flex xs4>
      <panel title="Song MetaData">
        <v-text-field
          label="Title"
          required
          :rules="[required]"
          v-model="song.title"
        ></v-text-field>

        <v-text-field
          label="Artist"
          required
          v-model="song.artist"
          :rules="[required]"
        ></v-text-field>

        <v-text-field
          label="Album"
          required
          :rules="[required]"
          v-model="song.album"
        ></v-text-field>

        <v-text-field
          label="Genre"
          required
          :rules="[required]"
          v-model="song.genre"
        ></v-text-field>

        <v-text-field
          label="Album Image Url"
          required
          :rules="[required]"
          v-model="song.albumImageUrl"
        ></v-text-field>

        <v-text-field
          label="Youtube Id"
          required
          :rules="[required]"
          v-model="song.youtubeId"
        ></v-text-field>
      </panel>
    </v-flex>
    <v-flex xs8>
      <panel title="songStructure" class="ml-4">
        <v-text-field
          label="Lyrics"
          multi-line
          required
          :rules="[required]"
          v-model="song.lyrics"
        ></v-text-field>

        <v-text-field
          label="Tab"
          multi-line
          required
          :rules="[required]"
          v-model="song.tab"
        ></v-text-field>
      </panel>

      <div class="danger-alert" v-if="error">
        {{ error }}
      </div>

      <v-btn
        class="cyan"
        dark
        @click="save">
        Save Song
      </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
  import Panel from '@/components/Panel'
  import SongsService from '@/services/SongsService'

  export default {
    data () {
      return {
        song: {
          title: null,
          artist: null,
          album: null,
          genre: null,
          albumImageUrl: null,
          youtubeId: null,
          lyrics: null,
          tab: null
        },
        error: null,
        required: (value) => !!value || 'Required.'
      }
    },
    methods: {
      async save () {
        console.log('clicked')
        this.error = null
        const areAllFieldsFilledIn = Object
          .keys(this.song)
          // effecient way to check for keys
          .every(key => !!this.song[key])
        if (!areAllFieldsFilledIn) {
          this.error = 'Please fill out all required fields'
          return
        }

        const songId = this.$store.state.route.params.songId

        try {
          await SongsService.put(this.song)
          this.$router.push({
            name: 'song',
            params: {
              songId: songId
            }
          })
        } catch (error) {
          console.log(error)
        }
      }
    },
    components: {
      Panel
    },
    async mounted () {
      try {
        const songId = this.$store.state.route.params.songId
        this.song = (await SongsService.show(songId)).data
      } catch (error) {
        console.log(error)
        // this.error = error.response.data.error
      }
    }
  }
</script>

<style scoped>

</style>
