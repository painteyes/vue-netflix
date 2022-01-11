<template>

  <div id="app">
    
    <Header @search='getSearch' />

    <Main :search='searchResult' />

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
      searchedText:"",
      searchResult:[],
    }
  },

  methods: {

    getSearch: function(searchingText){

      this.searchedText = searchingText;

      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '6362dd11ef9f4da66e17d4b0df63adb6',
          query: this.searchedText,
        }
      }).then ((response) => {
        this.searchResult = response.data.results;
      });

    }

  }

};

</script>


<style lang="scss">

@import './style/general.scss';

</style>
