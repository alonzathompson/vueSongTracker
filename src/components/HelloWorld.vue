<template>
  <div>
  <v-container fluid>
    <div class="hello">
      <h1>{{ msg }}</h1>
    </div>
  </v-container>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Vue Song Tracker'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.hello h1{
  color: white;
}
</style>
