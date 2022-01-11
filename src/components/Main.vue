<template>

    <section>

        <ul v-for = "(element, index) in search" :key='index'>
            <li  >
                {{ element.title }}
            </li>
            <li  >
                {{ element.original_title }}
            </li>
            <li  >
                {{ element.original_language }}
            </li>
            <li  >
                {{ element.vote_average }}
            </li>
        </ul>

    </section>

</template>

// -------------------------------------------------------------------

<script>

export default {

    name: 'Main',
    
    props: {
        search: Array,
    },

}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

section{
    
    background-color: gray;
    


    ul{
        border: 2px solid red;
        padding: 20px;
    }




}


</style>
