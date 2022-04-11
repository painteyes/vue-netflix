<template>
    <div class="slide">
        <img :src="`https://image.tmdb.org/t/p/w342/${poster}`" :alt="originalTitle" class="poster">
        <div class="description">
            <div class="container">
                <div class="small-logo">
                    <img src="../assets/images/logo.png" :alt="language"> 
                    <span>{{type == 'isMovie' ? 'MOVIE' : 'SERIES'}}</span>
                </div>
                <div>
                    <h1>{{title}}</h1>
                </div>
                <div class="overview">
                    <p>{{overview}}</p>
                </div>
            </div>
        </div>  
    </div>
</template>


<script>

export default {
    name: 'ContentInfo',
    data: function() {

        return {
            flagsList: ['it','en','fr'],
        }
    },
    props: {
        poster: String,
        title: String,
        overview: String,
        type: String
    },
}

</script>

<style scoped lang="scss" >

.slide{
    text-align: left;
    height:800px;
    position:relative;
    margin:5px;
    transition: 1s;
    .poster {
        height: 100%;
        width: 100%;
        object-fit:cover;
        object-position: bottom;
    }
    .description{
        background: linear-gradient(rgba(0,0,0,0), rgb(6,6,6));
        color: white;
        position:absolute;
        bottom:0;
        width:100%;
        height:100%;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        align-items: flex-start;  
        .container {
            padding-bottom: 50px;
            >* {
                margin-bottom: 10px;
            }
            .overview {
                width: 40%;
                text-align: left;
                font-size: 18px;
                font-family:  'roboto';
                font-weight: 300
            }
            .small-logo{
                span {
                    font-size: 14px;
                    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                }
                img{
                    width: 30px;
                }
            }
        }
    }
} 
</style>