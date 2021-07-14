<template>
<div class="container">
  <Search @searchN="getFilms"/>
  <div class="row">
      <div class="col-12"><h2>Films</h2></div>
  </div>
  <div class="row cards-row">
        <Card v-for="(item, index) in filmResults" :key="index" :det="item"/>
  </div>
  <div class="row">
      <div class="col-12"><h2>TV Series</h2></div>
  </div>
  <div class="row cards-row">
      <Card v-for="(item, index) in tvResults" :key="index" :det="item"/>
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
            tvResults:'',
            apiBase: 'https://api.themoviedb.org/3/',
            apiKey: '2467b66cc2e2dd66d129967969509c91'
        }
    },

    methods: {       

        getFilms( searchValue ){
            if ( searchValue) {
                this.searchValue = searchValue;
                this.filmResults = '';
                this.tvResults='';
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
                        
                        
                    })
    
                    .catch(error => {
                        console.log('Errore: ', error);
                    });
                
                axios
                    .get(this.apiBase+'search/tv', {
                        params:{
                            api_key: this.apiKey,
                            query: this.searchValue,
                            language: 'it-IT'
                        }
                        
                    })
    
                    .then(tav => {
                        this.tvResults = tav.data.results;
                        console.log(this.tvResults);
                        
                    })
    
                    .catch(error => {
                        console.log('Errore: ', error);
                    });
            } 
        },

    }
}




</script>

<style lang="scss" scoped>
.container {
        margin-top: 100px;
        h2 {
            color: white;
        }
        .cards-row{
            overflow-x: scroll;
            flex-wrap: nowrap;
        }
    }
</style>