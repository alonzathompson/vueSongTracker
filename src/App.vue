<template>
  <div id="app">
    <v-app>
      <page-header />
      <main id="background">
        <v-container fluid>
          <router-view />
        </v-container>
      </main>
    </v-app>
  </div>
</template>

<script>
  import PageHeader from '@/components/Header.vue'
  export default {
    name: 'app',
    components: {
      PageHeader
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#background {
  background: url('./assets/vueBackground2.jpg') no-repeat;
  background-size: cover;
}

.danger-alert {
  color: red;
}

</style>
