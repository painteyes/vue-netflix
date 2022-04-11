<template>
    <section>
            <div class="movie-card" v-for='(movie,index) in movies' :key="index">
                <Card 
                    :poster='movie.poster_path'
                    :title='movie.title'
                    :originalTitle='movie.original_title' 
                    :language='movie.original_language'
                    :vote='movie.vote_average'
                    :popularity='movie.popularity'
                />
            </div>
    </section>
</template>

<script>

import Card from './Card.vue';

export default {
    name:'MovieList',
    props:{
        movies: Array
    },
    components:{
        Card, 
    },
}
</script>

<style lang="scss" scoped>
section {
    display: flex;
    flex-wrap: wrap;
    .movie-card {
        margin: 5px;
        margin-left: 0;
        width: calc((100% / 4) - 5px);
        border-color: white;
    }   
}
</style>