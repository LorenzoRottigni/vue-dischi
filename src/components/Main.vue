<template>
    <main class="d-flex flex-column">
        <div class="logo-container bg-light p-3">
            <img src="./../assets/spotify-logo.png" alt="spotify logo">
        </div>
        <div class="container-fluid main-container py-5 flex-grow-1">
            <div class="row d-flex flex-wrap justify-content-center gap-3">
                <div class="card flex-shrink-0 col-3 col-md-2 px-0 shadow"
                v-for="(disc, index) in discs" :key="index">
                <img :src="disc.poster" class="card-img-top shadow" :alt="disc.title">
                <div class="card-body px-1 pt-1 d-flex flex-column">
                    <h5 class="card-title mt-3">{{disc.title}}</h5>
                    <p class="card-text">{{disc.author}}</p>
                    <div class="card-footer d-flex justify-content-between justify-self-end">
                        <h6>{{disc.genre}}</h6>
                        <h6>{{disc.year}}</h6>
                    </div>
                </div>
            </div>
            </div>
            
            
        </div>
    </main>
</template>

<script>

export default{
    name : 'Main',
    data(){
        return {
            discs : undefined
        }
    },
    beforeMount(){

    },
    mounted(){
        const axios = require('axios').default;
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            // handle success
            this.discs = response.data.response
            console.log(response);
        });
    }
}
</script>

<style scoped lang="scss">
    main{
        .logo-container{ 
            img{
                width: 70px;
                height: 70px;
            }
        }
        .main-container{
            background-color: #447daf;
            .card{
                padding-bottom: 2.5rem;
                background-color: #47b194;
                color: white;
                border: solid #47b194;
                img{
                    border-bottom: solid #47b194
                }
                h5{
                    font-size: 18px;
                    font-weight: normal;
                }
                .card-text{
                    color: #447daf;
                    font-weight: bold;
                }
                .card-footer{
                    position: absolute;
                    bottom: 0;
                    left: 0;
                    right: 0;
                    height: 2.5rem;
                }
            }
        }
    }
    
    
    
</style>