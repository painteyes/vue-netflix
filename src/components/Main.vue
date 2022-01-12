<template>

    <section>

        <!-- REMINDER: Creare un componente per le Card -->

        <h2>Film</h2>

        <ul v-for = "(element, index) in movieSearchResult" :key='index'>
            <li  >
                {{ element.title }}
            </li>
            <li  >
                {{ element.original_title }}
            </li>
            <li  >
                {{ getFlag() }}
            </li>
            <li  >
                {{ element.vote_average }}
                
            </li>
        </ul>

        <!-- <h2>Series</h2>

        <ul v-for = "(element, index) in movieSearchResult" :key='index'>
            <li  >
                {{ element.title }}
            </li>
            <li  >
                {{ element.original_title }}
            </li>
            <li  >
                {{ getFlag() }}
            </li>
            <li  >
                {{ element.vote_average }}
            </li>
        </ul> -->




    </section>

</template>

// -------------------------------------------------------------------

<script>

export default {

    name: 'Main',
    
    props: {

        movieSearchResult: Array,

    },

    methods: {

        getFlag: function(){

            this.movieSearchResult.forEach(element => {

                if (element.original_language === 'ita' || element.original_language === 'en' ) {
                    return "<img :src='require(" + "'../assets/" + element.original_language + ".svg')>"
                } else  {
                    return element.original_language
                }
            });               
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
