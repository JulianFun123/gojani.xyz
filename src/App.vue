<template>
  <div id="app">
    <navigation></navigation>
    <router-view id="main"/>
  </div>
</template>
<script>
import Navigation from "@/components/Navigation.vue";
import $ from "jdomjs";

export default {
  components: {
    "navigation": Navigation
  },
  created(){
    window.onscroll = function(){
        if (window.scrollY > 1) {
            $("#nav").css({
                paddingTop: "",
                boxShadow: "rgba(0, 0, 0, 0.55) 0px -45px 18px 34px"
            });
        } else {
            $("#nav").css({
                paddingTop: "20px",
                boxShadow: ""
            });
        }
    };

    setTimeout(() => {
      window.onscroll();
    }, 10);
    
  }
}
</script>
<style>
  #main {
    margin-top: 160px;
  }
</style>
