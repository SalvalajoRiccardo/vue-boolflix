<template>
<div  id="nav-bar">
    <div id="titolo">
        <h1>boolflix</h1>
    </div>
    <form>
        <input 
        type="text" 
        placeholder="Search"
        v-model.trim="inputText"
        >
        <button 
        type="submit" 
        @click.prevent="$emit('searchN',inputText)"
        ><i class="fas fa-search"></i>
        </button>
    </form>

</div>
  
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

<style lang="scss" scoped>
    #nav-bar{
        position: fixed;
        z-index: 500;
        top: 0;
        left: 0;
        width: 100%;
        height: 100px;
        background-color: #141414;
        display: flex;
        justify-content: space-between;
        align-items: center;
        
        h1{
            color: red;
            text-transform: uppercase;
            margin-left: 50px;
        }
        input {
           margin-right: 10px;
           border: 1px solid white;
           background-color: black; 
           color: white;
        }
        button {
            margin-right: 50px;
            color: white;
            border: none;
            background-color: #141414 ;
        }

    }
</style>
