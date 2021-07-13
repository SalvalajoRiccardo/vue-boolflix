<template>
  <div class="card">
        <h3>{{det.title}}</h3>
        <span>{{det.original_title}}</span>
        <p>Language:  
          <img v-if="flagsArray.includes(det.original_language)" class="flag" :src="require('../assets/img/'+det.original_language+'.png')" :alt="det.original_language">
          <span v-else>{{det.original_language}}</span>
        </p> 
        <span>Vote: {{det.vote_average}}</span>
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
 }
}
</script>

<style scoped lang='scss'>
    .card{
        .flag {
        width: 20px;
        }
        
    }   
</style>