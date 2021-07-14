<template>
  <div class="card">
      <div class="img-box">
            <h3 v-if="!det.poster_path" >{{det.title == null ? det.name : det.title}}</h3>
            <img v-if="det.poster_path" :src="'https://image.tmdb.org/t/p/w342/'+det.poster_path" :alt="det.title">
            <img v-else :src="require('../assets/img/notfound.png')" alt="not-found" >
      </div>

      <div class="info-box">
        <h3>{{det.title == null ? det.name : det.title}}</h3>
        <span><strong>Titolo Originale: </strong>{{det.original_title == null ? det.original_name : det.title}}</span>
        <p>Language:  
          <img v-if="flagsArray.includes(det.original_language)" class="flag" :src="require('../assets/img/'+det.original_language+'.png')" :alt="det.original_language">
          <span v-else>{{det.original_language}}</span>
        </p> 
        <p>Vote: <i v-for="(star,index) in stars(det.vote_average)" :key="index"  class="fas fa-star yellow-star"></i> </p>
        <p v-if="det.overview"><strong>Overweiw: </strong>{{det.overview}}</p>
      </div>
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
        background-color:#141414 ;
        border: none;
        width: 340px;
        margin: 0 10px;
        padding: 0;
        .info-box {
            color: white;
            position: absolute;
            padding: 15px;
            display: none;
            height:520px ;
            overflow: auto;
            .flag {
                width: 20px;
            }
            .yellow-star {
                color: gold;
            }

        }

        .img-box{
            img{
                height: 520px;
                width: 342px;
                object-fit: cover;
            }
            h3 {
                position: absolute;
                top: 15px;
                left: 15px;
                color: white;

            }
        }

        &:hover {
            .img-box {
                opacity: 20%;
                h3 {
                    display: none;
                }
            }
            .info-box {
                display: block;
            }
        }
    }   
</style>