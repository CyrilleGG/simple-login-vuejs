<template>
  <div id="app">
    <router-link v-if="auth" to="/" v-on:click.native="logout()" replace>Logout</router-link>
    <router-view @auth="setAuth" />
  </div>
</template>

<script>
import { data } from './db.js'

export default {
  name: 'App',

  data () {
    return {
      auth: false,
      data
    }
  },

  mounted () {
    if (!this.auth) {
      this.$router.replace({name: 'login'})
    }
  },

  methods: {
    setAuth (status) {
      this.auth = status
    },
    logout () {
      this.auth = false
    }
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
</style>
