<template>
  <div id="app">
    <Header
      @search='keywordSearch' 
      :genres="genresList" 
    />
    <Main
      :keyword='keyword'
      :movieList='movieSearchedList' 
      :seriesList='seriesSearchedList' 
    />
    <Footer  />
  </div>
</template>


<script>

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import Footer from "./components/Footer.vue";

import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    Main,
    Footer
  },
  data: function() {
    return {
      apiKey: '6362dd11ef9f4da66e17d4b0df63adb6',
      movieSearchedList:[],
      seriesSearchedList:[],
      keyword: false,
      genresList: [],
    }
  },
  methods: {
    keywordSearch: function(keyword){
      this.keyword = true;
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: keyword,
        }
      }).then ((response) => {
        this.movieSearchedList = response.data.results;
      });
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: keyword,
        }
      }).then ((response) => {
        this.seriesSearchedList = response.data.results;
      });
    },
    async genresApiCall() {
      await axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=${this.apiKey}&language=en-US`).then((response) => {
        this.genresList = response.data.genres;
      })
    },

  },
  mounted(){
      this.genresApiCall();
  }

};

</script>
<style lang="scss">

@import './style/general.scss';

</style>
