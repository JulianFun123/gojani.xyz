<template>
  <div id="app">
    <navigation></navigation>
    <router-view id="main"/>
  </div>
</template>
<script>
import Navigation from "@/components/Navigation.vue";

export default {
  components: {
    "navigation": Navigation
  },
  created(){
    
  }
}
</script>
<style>
  #main {
    margin-top: 100px;
    padding-left: 270px;
  }
</style>
