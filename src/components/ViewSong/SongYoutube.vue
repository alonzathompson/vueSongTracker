<template>
      <panel title="YouTube">
        <youtube
          :video-id="youtubeId"
          :player-width="300"
          :player-height="235">
        </youtube>
      </panel>
</template>

<script>
  import Panel from '@/components/Panel'

  export default {
    props: [
      'youtubeId'
    ],
    components: {
      Panel
    },
    async mounted () {
      await console.log(this.youtubeId)
    }
  }
</script>

<style scoped>

</style>
