<template>
  <div id="app">
    <button class="ui button" v-on:click="click">Test {{ c }}</button>

    <h4 v-if="movies[0]">{{ movies[0].titel }}</h4>
    <ul id="example-1" v-if="movies[0]">
      <li v-for="movie in movies" :key="movie.id">{{ movie.titel }}</li>
    </ul>
    <input v-if="movies[0]" v-model="movies[0].titel" placeholder="edit me">
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Yo  ur Vue.js App!",
      c: 0,
      movies: []
    };
  },
  methods: {
    click: function() {
      this.c++;
      axios
        .get(
          "https://my-json-server.typicode.com/devcronberg/json-server-film/film"
        )
        .then(v => {
          this.movies = v.data;
          console.log(v.data);
        });
    }
  }
};
</script>

<style lang="css">
</style>