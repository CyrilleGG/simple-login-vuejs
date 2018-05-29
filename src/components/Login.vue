<template>
  <div class="form-container">
    <h1>{{ msg }}</h1>
    <form action="">
      <input type="text" name="username" v-model="input.username" id="username" placeholder="Username">
      <input type="password" name="password" v-model="input.password" id="password" placeholder="Password">
      <input type="submit" value="Login" v-on:click="login()">
    </form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      msg: 'Welcome to Bac à sable',
      input: {
        username: '',
        password: ''
      }
    }
  },

  methods: {
    login () {
      if (this.input.username !== '' && this.input.password !== '') {
        for (var i = 0; i < this.$parent.data.length; i++) {
          if (this.input.username === this.$parent.data[i].username && this.input.password === this.$parent.data[i].password) {
            this.$emit('auth', true)
            this.$router.replace({name: 'welcome'})
            break
          } else {
            console.log('The username and / or the password is incorrect')
          }
        }
      } else {
        console.log('Please, enter a username and a password')
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  form {
    display: flex;
    flex-flow: column;
    justify-content: space-between;
    align-items: center;
    min-height: 20vh;
  }

  input {
    display: block;
    max-width: 10%;
  }
</style>
