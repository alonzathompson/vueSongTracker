<template>
  <v-layout column align-center justify-center row fluid fill-height>
    <v-flex >
      <panel title="Login">
        <v-text-field
          label="Email"
          v-model="email"
        > </v-text-field>
        <v-text-field
          label="Password"
          type="password"
          v-model="password"
        > </v-text-field>
        <br>
        <div class="danger-alert" v-html="error"></div>
        <br>
        <v-btn
          class="cyan" dark
          @click="login">Login
        </v-btn>
      </panel>
    </v-flex>
  </v-layout>
</template>

<script>
  import AuthenticationService from '@/services/AuthenticationService'
  import Panel from '@/components/Panel'
  export default {
    data () {
      return {
        email: '',
        password: '',
        error: null
      }
    },
    methods: {
      async login () {
        try {
          const response = await AuthenticationService.login({
            email: this.email,
            password: this.password
          })
          this.$store.dispatch('setToken', response.data.token)
          this.$store.dispatch('setUser', response.data.user)
          this.$router.push({
            name: 'songs'
          })
        } catch (error) {
          this.error = error.response.data.error
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
