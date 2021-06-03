<template>
  <div id="app">
    <div class="w-full max-w-xs mx-auto pt-32">
      <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" v-on:submit.prevent="onSubmit" >
        <div class="mb-4">
          <label class="block text-grey-darker text-sm font-bold mb-2" for="username">
            Username
          </label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker leading-tight focus:outline-none focus:shadow-outline"
            id="username" type="text" placeholder="Username">
        </div>
        <div class="mb-6">
          <label class="block text-grey-darker text-sm font-bold mb-2" for="password">
            Password
          </label>
          <input class="shadow appearance-none border border-red rounded w-full py-2 px-3 text-grey-darker mb-3 leading-tight focus:outline-none focus:shadow-outline"
            id="password" type="password" placeholder="******************">
          <p class="text-red text-xs italic">Please choose a password.</p>
        </div>
        <div class="flex items-center justify-between">
          <button class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
            type="submit">
            Sign In
          </button>
          <a class="inline-block align-baseline font-bold text-sm text-blue hover:text-blue-darker" href="#">
            Forgot Password?
          </a>
        </div>
      </form>
      <p class="text-center text-grey text-xs">
        ©2021 Captain Pangyo. All rights reserved.
      </p>
  </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data: function () {
    return {
        username : '',
        password : ''
    }
  },
  methods : {
    onSubmit : function(event) {
      event.preventDefault();

      var username = this.username;
      var password = this.password;

      var url = 'https://jsonplaceholder.typicode.com/users/';
      var body = JSON.stringify({
            name: username,
            password: password
      });

      axios.post(url, body)
      .then( response => {
        console.log(response);
      })
      .catch( error => {
        console.log(error);
      });

      this.username = '';
      this.password = '';
    }
  }
}
</script>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/0.7.4/tailwind.min.css"

</style>
