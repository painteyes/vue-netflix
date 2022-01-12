<template>
    <section>

        <div class="cover">

            <template v-if="isMovie">
               <img :src="'https://image.tmdb.org/t/p/w342'+ movieObject.poster_path" alt="">
            </template>

            <template v-if="isSeries">
               <img :src="'https://image.tmdb.org/t/p/w342'+ seriesObject.poster_path" alt="">
            </template>

        </div>

        <ul>

            <!-- title -->
            <li v-if="isMovie">
                Titolo: {{ movieObject.title }} 
            </li>

            <li v-if="isSeries">
                Titolo: {{ seriesObject.name }} 
            </li>
            
            <!-- original title -->
            <li v-if="isMovie">
                 Titolo: {{ movieObject.original_title }} 
            </li>

            <li v-if="isSeries">
                 Titolo: {{ seriesObject.original_name }} 
            </li>
            
            <!-- original language -->
            <li v-if="isMovie">

                <template v-if="flagsList.includes(movieObject.original_language)">
                    <img class="flag" :src="require(`../assets/${movieObject.original_language}.svg`)" alt="" >
                </template> 

                <template v-else>
                    Lingua: {{movieObject.original_language}}
                </template> 
            </li>

            <li v-if="isSeries">

                <template v-if="flagsList.includes(seriesObject.original_language)">
                    <img :src="require(`../assets/${seriesObject.original_language}.svg`)" alt="" >
                </template> 

                <template v-else>
                    Lingua: {{ seriesObject.original_language }}
                </template> 
            </li>

            <!-- vote -->
            <li v-if="isMovie">

                <!-- Voto: {{ getNumberOfStars(movieObject.vote_average) }} -->
                 
                <i class="fas fa-star" v-for="number,index in getNumberOfStars(movieObject.vote_average)" :key='index'></i>
                <i class="far fa-star" v-for="number,index in (5 - getNumberOfStars(movieObject.vote_average))" :key='index'></i>
                
            </li>

            <li v-if="isSeries">

                <!-- Voto: {{ getNumberOfStars(seriesObject.vote_average) }} -->

                <i class="fas fa-star" v-for="number,index in getNumberOfStars(seriesObject.vote_average)" :key='index'></i>
                <i class="far fa-star" v-for="number,index in (5 - getNumberOfStars(seriesObject.vote_average))" :key='index'></i>

            </li>

        </ul>  

    </section>
</template>

// -------------------------------------------------------------------

<script>

export default {

    name: 'SingleCard',

    data: function() {

        return {
            flagsList: ['it','en','fr'],
        }
    },
    
    props: {
        movieObject: Object,
        seriesObject: Object,
        isSeries: Boolean,
        isMovie: Boolean,
    },

    methods: {

        getNumberOfStars: function(vote) {
            return Math.ceil(vote/2);
        }
        
    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

section{

    border: 2px solid red;
    margin-right: 40px;
    margin-bottom: 40px;

    padding: 20px;
    // height: 300px;
    width: 200px ;
    
    ul{  
        // padding: 20px;
        // height: 300px;
        // width: 200px ;
    }

    .flag{
        width: 30px ;
    }

}

</style>