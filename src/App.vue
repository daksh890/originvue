<template>
  <HeaderPage/>
  <router-view></router-view>
  
</template>

<script>
import HeaderPage from './components/header.vue';


export default {
  name: 'App',
  components:{
    HeaderPage
  },
  
}
</script>


