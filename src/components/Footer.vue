<template>
    <footer>
        <div class="container">
            <!-- LOGO -->
            <div class="logo">
                <a href=""><img src="@/assets/images/logo-footer.png" alt="logo"></a>   
            </div>
            <div class="links">
                <div>
                    <h5>Languages</h5>
                    <ul>
                        <li>
                            <span>HTML</span>
                        </li>
                        <li>
                            <span>SCSS</span>
                        </li>
                        <li>
                            <span>JavaScript</span>
                        </li>
                        <li>
                            <a href="https://vuejs.org" target="_blank">Vue CLI</a>
                        </li>
                    </ul>
                </div>
                <div>
                    <h5>API and Libraries</h5>
                    <ul>
                        <li>
                            <a href="https://www.themoviedb.org" target="_blank">The Movie Database API</a>
                        </li>
                        <li>
                            <a href="https://www.npmjs.com/package/vue-slick-carousel" target="_blank">Vue Slick Carousel</a>
                        </li>
                        <li>
                            <a href="https://axios-http.com" target="_blank">Axios</a>
                        </li>
                        <li>
                            <a href="https://fontawesome.com" target="_blank">Font Awesome</a>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="socials">
                <a href="https://github.com/painteyes" target="_blank" class="icon">
                    <i class="fab fa-github"></i>
                </a>
                <a href="#" target="_blank" class="icon">
                    <i class="fab fa-instagram"></i>
                </a>
                <a href="#" target="_blank" class="icon">
                    <i class="fab fa-youtube"></i>
                </a>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style lang="scss" scoped>
footer {
    width: 100%;
    padding: 3rem;
    .container {
        display: flex;
        justify-content: space-between;
        .logo img{
            width: 150px;
        }
        a {
            transition: opacity .2s;
            cursor: default;
        }
        a:hover {
            opacity: .8;
            text-decoration: underline;
        }
        .socials {
            margin-bottom: 1rem;
            text-align: right;
            .icon {
                margin-right: 1rem;
                font-size: 1.5rem;
                color: white;
            }
        }
        .links {
            display: flex;
            justify-content: center;
            >* {
                margin-right: 40px;
            }
            h5 {
                color: white;
                font-size: 1rem;
            }
            ul {
                padding: 0;
                li {
                    padding: .5rem 0 0;
                    span, a {
                        color: rgba(255,255,255,0.5);
                        font-size: .9rem;
                        font-weight: 300;
                    }
                }
            }
        }
        .credits {
            padding-top: 2rem;
            color: rgba(255,255,255,0.4);
            font-weight: 200;
            font-size: .8rem;
            a {
                color: red;
            }
        }
    }
}
</style>