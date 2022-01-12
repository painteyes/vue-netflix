<template>
    <section>

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
                    <img :src="require(`../assets/${movieObject.original_language}.svg`)" alt="" >
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
                Voto: {{ movieObject.vote_average }}
            </li>

            <li v-if="isSeries">
                Voto: {{ seriesObject.vote_average }}
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

        // getFlag: function(){

        //     if ( this.flagsList.includes(this.movieObject.original_language) ) {
        //         return `<img :src="require('../assets/${this.movieObject.original_language}.svg')" alt="" >`
        //     } else  {
        //         return this.movieObject.original_language
        //     }            
        // }

        

    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

section{

    border: 2px solid red;
    margin-right: 40px;
    margin-bottom: 40px;
    
    ul{  
        padding: 20px;
        height: 300px;
        width: 200px ;
    }

    img{
        width: 30px ;
    }

}

</style>