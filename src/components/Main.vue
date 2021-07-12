<template>
  <Search @searchN="a"/>
</template>

<script>
// import axios from 'axios'
import Search from "@/components/Search";
export default {
    name: 'Main',
    components: {
        Search,
    },

    data(){
        return{
            searchValue:'',
        }
    },

    methods: {
     a(Input){
            this.searchValue =Input;
            console.log(this.searchValue);
        }
  }
}




</script>

<style>

</style>