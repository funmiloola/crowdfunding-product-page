<template>
  <div id="app">
   <img src="@/assets/images/image-hero-desktop.jpg" alt="logo">
   <crowd-funding/>
  </div>
</template>

<script>
import CrowdFunding from './components/CrowdFunding.vue'
export default {
  components: {
   CrowdFunding
  }
}
</script>

<style scoped>
*{
  margin:0;
}
img{
  position:relative;
  margin-top:-8px;
  margin-left:-8px;
  width:1400px;
}
@media(max-width:768px){
  img{
    background-image:url(@/assets/images/image-hero-mobile.jpg);
    width:100vw;
    height:145px;
  }
}
</style>
