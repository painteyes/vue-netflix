<template>

    <section>

        <div class="logo">
            <img src="https://logospng.org/download/netflix/logo-netflix-4096.png" alt="logo">       
        </div>

      <div class="searchbar">
            <button @click="$emit('search', searchingText)">Search</button>
            <input type="text" v-model="searchingText" >
      </div>

    </section>

</template>

// -------------------------------------------------------------------

<script>

export default {
    name: 'Header',
    data: function (){
        return {
            searchingText: '',
        }
    }
}

</script>

// -------------------------------------------------------------------

<style lang="scss" scoped>

template{
    background-color: black;
}

section{

    background-color: black;
    display: flex;
    justify-content: space-between;
    
    img{
        width: 100px;
        margin: auto 20px;
    }

    .searchbar {

        margin: auto 20px;

        button{
            padding: 2px 5px;
            margin: 0 10px;
            border-radius: 10px ;
        }
    }

}

</style>