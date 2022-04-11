<template>
    <!--MAIN-->
    <main>
        <ContentPreview v-if="movieList.length == 0 && seriesList.length == 0 && !keyword" />
        <div class="container" v-if="keyword"> 
            <div v-if="(movieList.length !== 0 || seriesList.length !== 0)">
                <h1>Search results</h1>
                <!--MOVIES-->
                <div v-if="movieList">
                    <h3>MOVIES</h3>
                    <MovieList :movies = "movieList"/>
                </div>
                <!-- SERIES -->
                <div v-if="seriesList">
                    <h3>TV SERIES</h3>
                    <TvSeriesList :series = "seriesList" />
                </div>
            </div> 
            <div v-else><h2 class="no-results">The search didn't return any results</h2></div>
        </div>
        <Recommendations v-else />
    </main>
</template>


<script>

import MovieList from './MovieList.vue';
import TvSeriesList from './TvSeriesList.vue';
import Recommendations from './Recommendations.vue';
import ContentPreview from './ContentPreview.vue';

export default {
    name: 'Main',
    components: {
        MovieList,
        TvSeriesList,
        Recommendations,
        ContentPreview
    },
    props: {
        movieList: Array,
        seriesList: Array,
        keyword: Boolean
    }
}

</script>


<style lang="scss" scoped>
    main{
        background-color: #141414;
        padding-bottom: 100px;
        color: whitesmoke;
        .container {
            padding-top: 150px;
            h3 {
                font-family: 'Roboto';
                font-weight: 300;
                margin-top: 40px;
            }
            h2.no-results{
                margin: 20px 0;
                font-size: 50px;
                height: 60vh;
            }
        }
    }
</style>
