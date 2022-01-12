<template>

  <div id="app">
    
    <Header @searchRequest='getSearch' />

    <Main :movieSearchResult='movieSearch' :seriesSearchResult='seriesSearch' />

  </div>

</template>


<script>

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

import axios from 'axios';

export default {

  name: "App",

  components: {
    Header,
    Main,
  },

  data: function() {
    return {
      apiKey: '6362dd11ef9f4da66e17d4b0df63adb6',
      // searchedText:"",
      movieSearch:[],
      seriesSearch:[],
    }
  },

  methods: {

    getSearch: function(searchingText){

      // this.searchedText = searchingText;

      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: searchingText,
        }
      }).then ((response) => {
        this.movieSearch = response.data.results;
      });

      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: searchingText,
        }
      }).then ((response) => {
        this.seriesSearch = response.data.results;
      });

    }

  }

};

</script>


<style lang="scss">

@import './style/general.scss';

</style>
