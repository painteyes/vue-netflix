<template>
    <!--CARD-->
    <div class="card">
        <!--Poster-->
        <img v-if="poster" :src="`https://image.tmdb.org/t/p/w342/${poster}`" :alt="originalTitle" class="poster">
        <img v-else src="@/assets/images/placeholder.png" alt="This image is not available" class="placeholder_image">
        <!--Show only with hover-->
        <div class="description">
           <div>
                <span>Title</span>
                <h1>{{title ? title : originalTitle}}</h1>
           </div>
            <div class="language">
                <h3>Language</h3>
                <img class="flag" v-if="getFlag(language)" :src="require(`../assets/${language}.svg`)" :alt="language"> 
                <h3 v-else>{{language}}</h3>
            </div>            
            <div class="vote">
                <h3>Vote</h3>
                <div class="stars">
                    <i v-for='(number,index) in roundNumber(vote)' :key="`movie-${index}`" class="fas fa-star"></i>
                    <i v-for="(number, index) in 5 - roundNumber(vote) " :key="index" class="far fa-star"></i>
                </div>  
            </div>   
        </div>
    </div>
</template>


<script>

export default {
    name: 'Card',
    data: function() {
        return {
            flagsList: ['it','en','fr'],
        }
    },
    props: {
        poster: String,
        title: String,
        originalTitle: String,
        language:String,
        vote: String,
    },
    methods: {
        getFlag(language){
            const languages = ["it","en", "fr"];
            return languages.includes(language) ? true : false;
        },
        roundNumber(number){
            return Math.ceil(number/2)
        }
    },
}

</script>

<style scoped lang="scss" >

.card{
    text-align: center;
    height:400px;
    position:relative;
    margin:5px;
    transition: 1s;
    background-color: #bbb;
    .poster {
        border-radius: 10px;
        height: 100%;
        width: 100%;
        object-fit:cover;
        object-position: center;
    }
    .placeholder_image{
        height:100%;
        width:100%;
        object-fit:cover;
        object-position: center;
    }
    .description{
        background-color:rgba(0, 0, 0, 0.685);
        color: white;
        position:absolute;
        bottom:0;
        width:100%;
        height:100%;
        display:none;
        >* {
            margin-bottom: 20px;
        }
        h3{
            font-size:18px;
        }
        .language {
            h3 {
                margin-right: 5px;
                vertical-align: center;
            }
            .flag {
                width: 40px;
                margin-bottom: 5px;
            }
        }   
    }
    &:hover{
        cursor:pointer;
        z-index:1;
    }
    &:hover .description{
        display: flex;
        flex-direction: column;
        justify-content: center;  
    } 
}  

</style>