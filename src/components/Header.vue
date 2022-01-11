<template>

    <section>

        <div class="logo">
            <img src="https://logospng.org/download/netflix/logo-netflix-4096.png" alt="logo">       
        </div>

      <div class="searchbar">
            <input v-model="searchedText" type="text">
      </div>

    </section>

</template>

// -------------------------------------------------------------------

<script>

export default {
    name: 'Header',
    data: function (){
        return {
            searchedText: '',
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
    }

}

</style>