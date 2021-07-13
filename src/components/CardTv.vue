<template>
  <div class="card">
    <img v-if="detTv.poster_path" :src="'https://image.tmdb.org/t/p/w342/'+detTv.poster_path" :alt="detTv.name">
        <h3>{{detTv.name}}</h3>
        <span>{{detTv.original_name}}</span>
        <p>Language:  
          <img v-if="flagsArray.includes(detTv.original_language)" class="flag" :src="require('../assets/img/'+detTv.original_language+'.png')" :alt="detTv.original_language">
          <span v-else>{{detTv.original_language}}</span>
        </p> 
        <span>Vote: <i v-for="(star,index) in stars(detTv.vote_average)" :key="index"  class="fas fa-star yellow-star"></i> </span>
  </div>
</template>

<script>
export default {
  name: 'CardTv',
  props: ['detTv'],
  data(){
    return{
      flagsArray: ['en','fr','it']
    }
  },
  methods: {
        stars(vote){
         return parseInt(Math.round(vote / 2))
        }  
    }
 
}
</script>

<style scoped lang='scss'>
    .card{
        .flag {
        width: 20px;
        }
        .yellow-star {
            color: gold;
        }
        
        
    }   
</style>