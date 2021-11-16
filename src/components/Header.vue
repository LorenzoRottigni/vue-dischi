<template>
    <header class="bg-light p-3 d-flex align-items-center justify-content-around">
        <img src="./../assets/spotify-logo.png" alt="spotify logo">
        <div class="input-group input-group-lg">
            <select name="filterType" id="filterType" class="rounded text-center" v-model="activeFilter" @change="$emit('genreFilter', activeFilter)">
                <option value="all" selected>All</option>
                <option :value="genre" :key="index" v-for="(genre, index) in genres">{{genre}}</option>
            </select>
            <input type="text" v-model="filterText" class="form-control" aria-label="Text input with dropdown button"
            @keyup="$emit('search', filterText)"/>
        </div>
    </header>
</template>
<script>
export default{
    name : 'Header',
    data(){
        return {
            filterText : undefined,
            activeFilter : 'all'
        }
    },
    props: {
        genres: Array,
    },
    methods: {
        setActiveFilter(){

        }
    }
}
</script>
<style scoped lang="scss">
    img{
        width: 70px;
        height: 70px;
    }
    .input-group{
        max-width: 50%;
    }
    select{
        background-color: #447daf;
        color: white;
        margin-right: -2px
    }
</style>