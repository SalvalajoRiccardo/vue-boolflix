<template>
  <form>
      <div>
          <input 
          type="text" 
          placeholder="Cerca"
          v-model.trim="inputText"
          >
      </div>
      <div>
          <button 
          type="submit" 
          @click.prevent="$emit('searchN',inputText)"
          >Search</button>
      </div>
  </form>
  
</template>

<script>
export default {
    name:'Search',
    data() {
        return {
            inputText:''
        }
    },
    methods: {
        
    }
}
</script>

<style>

</style>
