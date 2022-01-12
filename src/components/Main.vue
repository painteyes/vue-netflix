<template>

    <section>

        <!-- REMINDER: Creare un componente per le Card -->

        <h2>Film</h2>

        <SingleCard v-for='element,index in movieSearchResult' :key='index' :movieObject='element' />

        <h2>Series</h2>

        <SingleCard />

    </section>

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

    },

    methods: {


    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>



</style>
