<template>
    <section>

        <div class="cover"> 

            <!-- Front -->
            <div class="cover-front">

                <template v-if="isMovie">
                    <img v-if="movieObject.poster_path" :src="'https://image.tmdb.org/t/p/w342'+ movieObject.poster_path" alt="">
                    <h2 v-else>{{movieObject.title}}</h2>
                </template>

                <template v-if="isSeries">
                    <img v-if="seriesObject.poster_path" :src="'https://image.tmdb.org/t/p/w342'+ seriesObject.poster_path" alt="">
                    <h2 v-else>{{seriesObject.name}}</h2>
                </template>
            </div>

            <!-- Retro -->
            <div class="cover-retro">

                <ul>

                    <!-- Title -->
                    <li v-if="isMovie">
                        <span>Titolo: </span> {{ movieObject.title }} 
                    </li>

                    <li v-if="isSeries">
                        <span>Titolo: </span> {{ seriesObject.name }} 
                    </li>
                    
                    <!-- Original title -->
                    <li v-if="isMovie">
                        <span>Titolo originale: </span> {{ movieObject.original_title }} 
                    </li>

                    <li v-if="isSeries">
                        <span>Titolo originale: </span> {{ seriesObject.original_name }} 
                    </li>
                    
                    <!-- Language -->
                    <li v-if="isMovie">

                        <template v-if="flagsList.includes(movieObject.original_language)">
                            <span>Lingua: </span>
                            <img class="flag" :src="require(`../assets/${movieObject.original_language}.svg`)" alt="" >
                        </template> 

                        <template v-else>
                            <span>Lingua: </span> {{movieObject.original_language}}
                        </template> 
                    </li>

                    <li v-if="isSeries">

                        <template v-if="flagsList.includes(seriesObject.original_language)">
                            <span>Lingua: </span>
                            <img class="flag" :src="require(`../assets/${seriesObject.original_language}.svg`)" alt="" >
                        </template> 

                        <template v-else>
                            <span>Lingua: </span> {{ seriesObject.original_language }}
                        </template> 
                    </li>

                    <!-- Vote -->
                    <li v-if="isMovie">
                        
                        <i class="fas fa-star" v-for="number,index in getNumberOfStars(movieObject.vote_average)" :key='index'></i>
                        <i class="far fa-star" v-for="number,index in (5 - getNumberOfStars(movieObject.vote_average))" :key='index'></i>
                        
                    </li>

                    <li v-if="isSeries">

                        <i class="fas fa-star" v-for="number,index in getNumberOfStars(seriesObject.vote_average)" :key='index'></i>
                        <i class="far fa-star" v-for="number,index in (5 - getNumberOfStars(seriesObject.vote_average))" :key='index'></i>

                    </li>

                    <!-- Overview -->
                    <li v-if="isMovie">
                        <span>Overview: </span>{{ movieObject.overview }} 
                    </li>

                    <li v-if="isSeries">
                        <span>Overview: </span> {{ seriesObject.overview }} 
                    </li>
                </ul>  
            </div>
        </div>
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

    width: 300px;
    height: 400px;
    margin-right: 10px;
    margin-bottom: 40px;

    .cover{

        height: 100%;
        background-color: black;
        color: white;
        border: 1px solid white;

        .cover-front{
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;

            img{
                height: 100%;
                width: 100%;
                object-fit: scale-down;
            }

            h2{
                width: 100%;
                text-align: center;
            }
        }

        .cover-retro{

            display: none;
            padding: 10px;

            .flag{
                width: 30px ;
                vertical-align: middle;
                padding-left: 5px ;
            }

            span{
                font-weight: bold;
                color: whitesmoke;
            }

        }

    }

    .cover:hover {

        cursor: pointer;
        overflow-y: auto;

        .cover-front {
            display: none;
        }

        .cover-retro {
            display: block;
        }  
    }

}

</style>