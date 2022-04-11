<template>
    <section>
        <!--SLIDER MOVIES-->
        <VueSlickCarousel v-if="popularMovies.length > 0"  v-bind="settings">
        <div v-for='movie in popularMovies' :key="movie.id" >
            <ContentInfo 
                v-if="movie.poster_path"
                :poster='movie.poster_path'
                :title='movie.title'
                :overview='movie.overview'
                :type= "'isMovie'"
            />
        </div>
        <div v-for='series in popularSeries' :key="series.id" >
            <ContentInfo
                v-if="series.poster_path"
                :poster='series.poster_path'
                :title='series.name'
                :overview='series.overview'
                :type= "'isSeries'"
            />
        </div>
        </VueSlickCarousel>
    </section>
</template>

<script>

import axios from 'axios';
import ContentInfo from './ContentInfo.vue';
import VueSlickCarousel from 'vue-slick-carousel';
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name:'ContentPreview',
    components:{
        ContentInfo,
        VueSlickCarousel,
    },
    data(){
        return{
            popularMovies:[],
            popularSeries:[],
            //CAROUSEL SETTINGS
            settings:{
                arrows: false,
                dots: true,
                infinite: false,
                rows: 1,
                speed: 500,
                slidesToShow: 1,
                focusOnSelect:true,
                autoplay:true,
                autoplaySpeed: 6000,
            }
        }
    },
    methods:{
        getPopular(){
            //MOVIES CALL
            axios.get('https://api.themoviedb.org/3/movie/popular?api_key=5ac3e59b84003d2645abcdbaac824d36&language=en-US&page=1')
            .then(result=>{
                this.popularMovies = result.data.results
            })
            .catch(error => console.log(error));
            //TVSERIES CALL 
            axios.get('https://api.themoviedb.org/3/tv/popular?api_key=5ac3e59b84003d2645abcdbaac824d36&language=en-US&page=1')
            .then(result=>{
                this.popularSeries = result.data.results
            })
            .catch(error => console.log(error));
        }
    },
    created(){
        this.getPopular();
    }
}
</script>

<style lang="scss" scoped>

</style>