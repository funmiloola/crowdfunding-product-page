<template>
  <div class="sidebar">
    <div class="overlay">
    <nav>
  <ul>
    <li>About</li>
    <li>Discover</li>
    <li>Get Started</li>
  </ul>
  </nav>
  </div>
  </div>
</template>

<script>
export default {
  
}
</script>
<style scoped>
  .overlay{
  position: fixed;
    top:0;
    left:0;
    width:100%;
    height: 100%;
    background: rgba(127, 126, 126, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}  
nav{
  background:#fff;
  width:85%;
  top:40px;
  left:20px;
  position:absolute;
  border-radius:8px;
  z-index:1500;
}
ul{
  padding-left:0;
  margin-bottom:1.5rem;
  margin-top:-0.5rem;
  
}

@media(max-width:768px){
  ul{
    display:block;
  }
}
li{
    list-style-type: none;
    padding-top:1rem;
    font-weight:bold;
    padding-left:8px;
}
li:not(:last-child){
  content:"";
  border-bottom:1px solid rgb(214, 212, 212);
  padding-bottom:1rem;
}
</style>
