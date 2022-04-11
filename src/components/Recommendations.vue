<template>
    <section>
    <!--SLIDER MOVIES-->
    <div class="container">
        <div class="list-title"><span>POPULAR</span><h1>MOVIE TITLES</h1></div>
            <VueSlickCarousel v-if="popularMovies.length > 0"  v-bind="settings">
                <div v-for='(movie,index) in popularMovies' :key="`movie-${index}`" >
                    <Card 
                        :poster='movie.poster_path'
                        :title='movie.title'
                        :originalTitle='movie.original_title' 
                        :language='movie.original_language'
                        :vote='movie.vote_average'
                        :popularity='movie.popularity'
                    />
                </div>
            </VueSlickCarousel>
        </div>
        <!--SLIDER SERIES-->
        <div class="container">
            <div class="list-title"><span>POPULAR</span> <h1>TV SERIES</h1></div>
            <VueSlickCarousel v-if="popularSeries.length > 0" v-bind="settings">
                <div v-for='(series,index) in popularSeries' :key="`tv-${index}`">
                    <Card 
                    :poster='series.poster_path'
                    :title='series.title'
                    :originalTitle='series.original_name' 
                    :language='series.original_language'
                    :vote='series.vote_average'
                    />
                </div>
            </VueSlickCarousel>
        </div>
    </section>
</template>

<script>
//API, COMPONENTS AND CAROUSEL
import axios from 'axios';
import Card from './Card.vue';
import VueSlickCarousel from 'vue-slick-carousel';
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
name:'Recommendations',
components:{
    Card,
    VueSlickCarousel,
},
data(){
    return{
        popularMovies:null,
        popularSeries:null,

        //CAROUSEL SETTINGS
        settings:{
            arrows: true,
            dots: true,
            infinite: false,
            rows: 1,
            speed: 500,
            slidesToShow: 5,
            focusOnSelect:true,
            autoplay:true,
            autoplaySpeed: 3000,
        }
    }
},
created(){
    this.getPopular();
},
methods:{
    //POPULAR
    getPopular(){
    //MOVIES CALL
    axios.get('https://api.themoviedb.org/3/movie/popular?api_key=5ac3e59b84003d2645abcdbaac824d36&language=en-US&page=1')
    .then(result=>{
        //assigning data of API to movielist, we can refer to the array as movieList now
        this.popularMovies = result.data.results
    })
    .catch(error => console.log(error));

    //TVSHOW CALL with axios
    axios.get('https://api.themoviedb.org/3/tv/popular?api_key=5ac3e59b84003d2645abcdbaac824d36&language=en-US&page=1')
    .then(result=>{
        //assigning data of API to tvlist, we can refer to the array as tvList now
        this.popularSeries = result.data.results
    })
    .catch(error => console.log(error));
        
    },
    }
}
</script>

<style lang="scss" scoped>
section {
    // padding: 50px;
}
.container{
    // padding: 50px;
    margin: 50px auto 60px;
}
.list-title {
    color: whitesmoke;

    h1{
        font-family: roboto;
        font-weight: 300;
        display: inline-block;

    }

    span {
        font-weight: bold;
        font-size: 35px;
        margin-right: 15px;
    }
}

</style>