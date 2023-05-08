<template>
    <div class="filter-box">
        <input type="text" placeholder="type tag to search" v-model="category"/>
        <button @click="$emit('filter', this.category)">search</button>
    </div>
</template>
<script>
    export default {
        name:'filterComponent',
        data(){
            return{
                category:"all",
            }
        },
        props:{
            tasks:Array,
        },
       
    }
</script>
<style scoped>
    
    input{
        width:20rem;
        padding: 0.5rem;
        border-radius:20px;
        margin-right: 1rem;
    }
    button{
        cursor:pointer;
        width:6rem;
        border-radius:20px;
        color:white;
        font-weight:bold;
        background: black;
        text-align: center;
        padding:0.5rem

    }
    

</style>