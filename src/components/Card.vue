<template>
  <div class="card">
        <img v-if="det.poster_path" :src="'https://image.tmdb.org/t/p/w342/'+det.poster_path" :alt="det.title">
        <h3>{{det.title}}</h3>
        <span>{{det.original_title}}</span>
        <p>Language:  
          <img v-if="flagsArray.includes(det.original_language)" class="flag" :src="require('../assets/img/'+det.original_language+'.png')" :alt="det.original_language">
          <span v-else>{{det.original_language}}</span>
        </p> 
        <span>Vote: <i v-for="(star,index) in stars(det.vote_average)" :key="index"  class="fas fa-star yellow-star"></i> </span>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['det'],
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