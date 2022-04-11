<template>
    <section>
            <div class="series-card" v-for='(series,index) in series' :key="index">
                <Card 
                    :poster='series.poster_path'
                    :title='series.name'
                    :language='series.original_language'
                    :vote='series.vote_average'
                    :popularity='series.popularity'
                />
            </div>
    </section>
</template>

<script>

import Card from './Card.vue';

export default {
    name:'TvSeriesList',
    props:{
        series: Array
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
    .series-card {
        margin: 5px;
        margin-left: 0;
        width: calc((100% / 4) - 5px);
    }   
}

</style>