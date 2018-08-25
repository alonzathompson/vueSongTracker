<template>
  <panel title="search">
    <v-text-field
      label="Search by song title, artist, album, genre"
      v-model="search"
    ></v-text-field>
  </panel>
</template>

<script>
  import Panel from '@/components/Panel'
  import _ from 'lodash'
  export default {
    data () {
      return {
        search: ''
      }
    },
    watch: {
      search: _.debounce(async function (value) {
        const route = {
          name: 'songs'
        }
        // url watches search text field
        if (this.search !== '') {
          route.query = {
            search: this.search
          }
        }
        this.$router.push(route)
        console.log(value)
      }, 700),
      // search text-field watches url
      '$route.query.search': {
        immediate: true,
        handler (value) {
          this.search = value
        }
      }
    },
    components: {
      Panel
    }
  }
</script>

<style scoped>
</style>
