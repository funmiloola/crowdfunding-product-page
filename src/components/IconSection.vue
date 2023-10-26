<template>
  <div v-if="showIcon" @click="toggleSidebar">
  <img src="@/assets/images/icon-hamburger.svg" alt="hamburger" v-if="currentIcon" @click="toggleIcon">
  <img src="@/assets/images/icon-close-menu.svg" alt="icon-close" v-else @click="toggleIcon">
  </div>
</template>

<script>
export default {
  props:{
   showIcon:Boolean,
   toggleSidebar:Function,
  },
  data (){
    return{
      currentIcon:true,
    }
  },
  methods:{
    toggleIcon(){
      this.currentIcon =! this.currentIcon;
    }
  }
}
</script>
<style scoped>
img{
  position:absolute;
  top:18px;
  right:6px;
  z-index:1500;
 
}
</style>