<template>
  <div id="app">
    <login></login>
    <socialMedia></socialMedia>
    
  </div>


</template>

<script>
import Footer from './footer.vue'
import login from './login.vue'
import socialMedia from './socialMedia.vue'


export default {
  components: {
    Footer,
    login,
    socialMedia,
   
  }
}
  
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  
}
</style>
