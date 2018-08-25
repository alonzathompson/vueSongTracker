<template>

    <v-container fluid class="white elevation-2">
      <v-toolbar flat dense class="cyan" dark>
        <v-toolbar-title>
          {{title}}
        </v-toolbar-title>
        <slot name="action" />
      </v-toolbar>

      <div class="pl-4 pr-4 pt-2 pb-2">
        <slot>
          no slot content defined
        </slot>
      </div>
    </v-container>

</template>

<script>
  export default {
    props: [
      'title'
    ]
  }
</script>

<style scoped>

</style>
