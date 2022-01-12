<template>

    <div class="main-container">

        <section class="movies">

            <h2>Film</h2>
            <div class="cards">
                <SingleCard 
                v-for='element,index in movieSearchResult' :key='index' 
                :movieObject='element' 
                :isMovie='true' />
            </div>

        </section>

        <section class="series">

            <h2>TV Series</h2>
            <div class="cards">
                <SingleCard v-for='element,index in seriesSearchResult' :key='index' 
                :seriesObject='element' 
                :isSeries='true' />
            </div>
            
        </section>

    </div>
    
</template>

// -------------------------------------------------------------------

<script>

import SingleCard from './SingleCard.vue';

export default {

    name: 'Main',

    components: {
        SingleCard,
    },
    
    props: {
        movieSearchResult: Array,
        seriesSearchResult: Array,
    },

    methods: {


    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

    .main-container{
        width: 90%;
        margin: auto;

        h2{
            margin: 20px 0;
            font-size: 50px;
        }
    }

    .movies,
    .series {
        margin-bottom: 50px;        
    }

    .cards{
        display: flex;
        flex-wrap: wrap;
    }

</style>
