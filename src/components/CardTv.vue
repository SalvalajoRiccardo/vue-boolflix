<template>
  <div class="card">
        <h3>{{detTv.name}}</h3>
        <span>{{detTv.original_name}}</span>
        <p>Language:  
          <img v-if="flagsArray.includes(detTv.original_language)" class="flag" :src="require('../assets/img/'+detTv.original_language+'.png')" :alt="detTv.original_language">
          <span v-else>{{detTv.original_language}}</span>
        </p> 
        <span>Vote: {{detTv.vote_average}}</span>
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