<template>
<div>
  <Search @searchN="a"/>
  <ul>
      <li v-for="(item, index) in filmResults" :key="index">{{item.title}}</li>
  </ul>

</div>
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
            filmResults:'',
            apiBase: 'https://api.themoviedb.org/3/',
            apiKey: '2467b66cc2e2dd66d129967969509c91'
        }
    },

    created() {
    
    //    this.getFilms()
    },

    computed : {
        getFilms(){
            if (this.searchValue) {
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
    },

    methods: {
        a(Input){
            this.searchValue =Input;
        },

       
  }
}




</script>

<style>

</style>