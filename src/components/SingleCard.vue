<template>

    <section>

        <ul>

            <li>
                {{ movieObject.title }}
            </li>

            <li>
                {{ movieObject.original_title }}
            </li>

            <li>
                {{ getFlag() }}
            </li>

            <li>
                {{ movieObject.vote_average }}
            
                
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

    },

    methods: {

        getFlag: function(){

            if ( this.flagsList.includes(this.movieObject.original_language) ) {
                return `<img :src="require('../assets/${this.movieObject.original_language}.svg')" alt="" >`
            } else  {
                return this.movieObject.original_language
            }            
        }

    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

section{

    ul{
        border: 2px solid red;
        padding: 20px;
    }

}

</style>