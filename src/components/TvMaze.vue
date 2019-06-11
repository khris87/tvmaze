<template>
    <div id="tvmaze">
        <input type="text" v-model="search" @keyup="load" placeholder="tapez votre recherche">
        <hr>
        <div
                v-for="info in infos"
                class="info media border p-3 my-3"
        >
            <img :src="info.show.image.medium" class="mr-3 mt-3 img-thumbnail">
            <div class="media-body text-left mt-3">
                <h3>{{info.show.name}}</h3>
                <span>Visitez le site officiel de la série : </span><a :href="info.show.officialSite">{{info.show.name}}</a>
                <div><b>Genre</b> : {{info.show.genres[0]}}, {{info.show.genres[1]}}</div>
                <small>{{info.show.status}}</small>

                <div v-html="info.show.summary"></div>
            </div>
        </div>
        <hr>
    </div>
</template>

<script>
    const axios = require('axios');
    export default {
        name: "TvMaze",
        data () {
            return {
                infos: [],
                search: ''
            }
        },
        methods:{
            load(){
                const query = this.search;
                axios
                    .get('http://api.tvmaze.com//search/shows?q='+query)
                    .then(response => (this.infos = response.data))
            }
        }
    }


</script>


<style scoped>

</style>