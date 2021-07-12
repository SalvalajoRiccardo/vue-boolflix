<template>
<div>
  <Search @searchN="getFilms"/>
  <div class="cards-box">
    <Card v-for="(item, index) in filmResults" :key="index" :det="item"/>
  </div>
 
</div>
</template>

<script>
import axios from 'axios'
import Search from "@/components/Search";
import Card from "@/components/Card";
export default {
    name: 'Main',
    components: {
        Search,
        Card,
    },

    data(){
        return{
            searchValue:'',
            filmResults:'',
            apiBase: 'https://api.themoviedb.org/3/',
            apiKey: '2467b66cc2e2dd66d129967969509c91'
        }
    },

    methods: {       

        getFilms( searchValue ){
            if ( searchValue) {
                this.searchValue = searchValue
                axios
                    .get(this.apiBase+'search/movie', {
                        params:{
                            api_key: this.apiKey,
                            query: this.searchValue,
                            language: 'it-IT'
                        }
                        
                    })
    
                    .then(res => {
                        this.filmResults = res.data.results;
                        console.log(this.filmResults);
                        
                    })
    
                    .catch(error => {
                        console.log('Errore: ', error);
                    });
                  
            } 
        },
  }
}




</script>

<style lang= 'scss'>
    /* .cards-box{
    } */
</style>