<template>
  <div class="card">
      <h3>{{det.title}}</h3>
      <span>{{det.original_title}}</span>
      <span>Language: {{det.original_language}}</span>
      <span>Vote: {{det.vote_average}}</span>
  </div>
</template>

<script>
export default {
 name: 'Card',
 props: ['det']
}
</script>

<style scoped lang='scss'>
    .card{

        span {
            display: block;
        }
    }
</style>