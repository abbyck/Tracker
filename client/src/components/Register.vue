<template>
  <v-layout column>
      <v-flex xs6 offset-xs3>
        <div class="white elevation-2">
          <v-toolbar flat dense class="cyan" dark>
            <v-toolbar-title>Register</v-toolbar-title>
          </v-toolbar>
          <div class="pl-4 pr-4 pt-2 pb-2">
            <v-form>
              <v-text-field
                label="Email"
                v-model="email"
                required
              ></v-text-field>
              <v-text-field
                type="password"
                label="Password"
                v-model="password"
                required
              ></v-text-field>
            </v-form>
            <v-btn class="cyan" @click="register" >Register</v-btn>
          <br>
          <div class="error" v-html="error" />
          </div>
        </div>
      </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  name: 'HelloWorld',
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        console.log(response.data)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.error{
    color: red;
}


</style>