<template>
  <Search @searchN="a"/>
</template>

<script>
import axios from 'axios'
import Search from "@/components/Search";
export default {
    name: 'Main',
    components: {
        Search,
    },

    data(){
        return{
            searchValue:'',
            apiBase: 'https://api.themoviedb.org/3/',
            apiKey: '2467b66cc2e2dd66d129967969509c91'
        }
    },

    created() {
        this.getFilms()
    },

    methods: {
        a(Input){
            this.searchValue =Input;
            console.log(this.searchValue);
        },

        getFilms(){
            axios
                .get(this.apiBase+'search/movie?', {
                    params:{
                        api_key: this.apiKey,
                        query: this.searchValue,
                        lenguage: 'it-IT'
                    }
                    
                })

                .then(resp => {
                    console.log(resp);
                    
                })

                .catch(error => {
                    console.log('Errore: ', error);
                });
        },
  }
}




</script>

<style>

</style>