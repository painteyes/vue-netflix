<template>
    <header> 
        <div class="header-content" :class="{'active' : this.handleScroll}" >
            <!-- LEFT -->
            <div class="header-left">
                <!-- LOGO -->
                <div class="logo">
                    <a href=""><img src="@/assets/images/logo.png" alt="logo"></a>   
                </div>
                <!-- NAVBAR -->
                <nav>
                <ul>
                    <li v-for="(link,index) in menuLinks" :key='index'>
                        <a href='#'>{{link}}</a>
                    </li>
                    <!-- SELECT GENRES -->
                    <!-- <li>
                        <select name="genres" v-model="selectedGenre" @change="$emit('filterGenres', selectedGenre)">
                        <option value='' disabled>Genere</option>
                        <option value="all">All</option>
                        <option
                        v-for="genre in genres"
                        :key="genre.id"
                        :value="genre.id"
                        >
                            {{genre.name}}
                        </option>
                        </select>
                    </li> -->
                    <li class="genres">                        
                        <select name="genres" v-model="selectedGenre">
                            <option v-if='!selectedGenre' value='' disabled>Genres</option>
                            <option value="all">All</option>
                            <option
                            v-for="genre in genres"
                            :key="genre.id"
                            :value="genre.id"
                            >
                                {{genre.name}}
                            </option>
                        </select>
                    </li>
                    <li>
                        <a href='#'>My List</a>
                    </li>
                </ul>
                </nav>
            </div>
            <!-- RIGHT -->
            <div class="header-right">
                <!-- INPUT AREA -->
                <div class="search">
                    <i class="fas fa-search" :class="{'active' : keywordSearch !== ''}"></i>
                    <input
                        type="text"
                        placeholder="Search a movie or TV series"
                        v-model="keywordSearch"
                        @keyup.enter="$emit('search', keywordSearch)"
                    />
                    <div class="button" @click="$emit('search', keywordSearch)"></div>
                </div>
                <!-- USER -->
                <div class="user">
                    <i class="far fa-bell"></i>
                    <img src="../assets/images/user.png" alt="">
                </div>
            </div>
        </div>
    </header>
</template>

<script>

export default {
    name: 'Header',
    props: {
        genres: Array,
    },
    data: function (){
        return {
            keywordSearch: '',
            menuLinks: ['Home', 'Series', 'Movies'],
            handleScroll: false,
            selectedGenre: ''
        }
    },
    methods: {
        setHandleScroll: function() {
            this.handleScroll = true;
        }
    },
    created: function() {
        window.addEventListener('scroll', this.setHandleScroll);
    }
}

</script>


<style lang="scss" scoped>

@import '@/style/variables.scss';

header {
    width: 100%;
    position: fixed;
    top: 0;
    z-index: 2;
    .header-content{
        background: linear-gradient(rgb(6,6,6), rgba(0,0,0,0));
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px 25px;
        &.active {
            background: linear-gradient(rgb(6,6,6), rgba(5,5,5,0.5));
        } 
        .header-left{
            display: flex;
            align-items: center;
            .logo {
                width: 50px;
            } 
            nav {
                ul {
                    display: flex;
                    align-items: center;
                    li {
                        padding: 0 20px;
                    }
                    li.genres {
                        color: $secondary-text-color;
                        select {
                            margin-left: 10px;
                            color: $secondary-text-color;
                            background: transparent;
                            border: 0;
                            outline: none;
                            // width: 150px;
                            cursor: pointer;
                            -webkit-appearance: none;
                            -moz-appearance: none;
                            appearance: none;
                            &:hover{
                                color: $primary-text-color;
                            }
                            option {
                                color: black;
                                // background-color: transparent;
                            }
                        }
                    }
                    a {
                        color: $secondary-text-color;
                        text-decoration: none;
                        cursor: pointer;
                        &:hover{
                            color: $primary-text-color;
                        }
                    }
                }
            }
        }
        .header-right {
            display: flex;
            align-items: center;
            .search {
                position: relative;
                i {
                    position: absolute;
                    left: 5px;
                    bottom: 20px;
                    font-size: 20px;
                    font-weight: 600 ;
                    color: rgba($color: rgb(255, 255, 255), $alpha: 0.5);
                    &.active{
                        color: whitesmoke;
                    }
                }
                input {
                    width: 320px;
                    padding: 10px 45px ;
                    background: transparent;
                    color: white;
                    border: 0;
                    border-bottom:  1px solid whitesmoke;
                    outline: none;
                    font-size: 17px ;
                }
            }
            .user {
                margin: 0 20px;
                .fa-bell {
                    font-size: 25px;
                    color: white;
                    margin: 0 25px;
                    &:hover {
                        cursor: pointer;
                    }
                }   
            }
            img {
                width:40px;
                height:40px;
                border-radius:10px;
                &:hover {
                    cursor: pointer;
                }
            }
        }  
    }  
}
</style>
