<template>
  <div>
   <main>
    <div class="header">
    <h1>About this project</h1>
    <p>The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform that elevates your screen to a more comfortable viewing height.Placing your monitor at eye level has the potential to improve your posture and make you more comfortable while at work, helping you stay focused on the task at hand.</p>
    <p>Featuring artisan craftsmanship,the simplicity of design creates extra desk space below your computer to allow notepads,pens,and USB sticks to be stored under the stand.</p>
    </div>
    <div id="details"  v-for="title in titles" v-bind:key="title.index">
        <div  :class="{'details':title.amount === 0}">
    <div class="title">
        <h2>{{title.name}}</h2>
        <h3>{{title.pledge}}</h3>
    </div>
    <p>{{title.contents}}</p>
    <div class="amount-section">
        <strong>{{title.amount}}  <span>{{title.span}}</span></strong>
        <button>{{title.button}}</button>
    </div>
    </div>
    </div>
   </main>
  </div>
</template>

<script>

export default {
  components: {
   
  },
  data(){
    return{
        titles:[
            {id:1, name:'Bamboo Stand', pledge:'Pledge $25 or more', contents:"You get an ergonomic stand made of natural bamboo.You've helped us launch our promotional campaing,and you'll be added to a special Backer member list.", amount:101, span:'left', button:'Select Reward'},
            {id:2, name:'Black Edition Stand', pledge:'Pledge $75 or more',contents:"You get a Black Special Edition computer stand and a personal thank you.You'll be added to our Backer member list Shipping is included.", amount:64,  span:'left', button:'Select Reward'},
            {id:3, name:'Mahogany Special Edition',pledge:'Pledge $200 or more', contents:"You get two Special Edition Mahogany stands,a Backer T-Shirt and a personal thank you.You'll be added to our Backer member list.Shipping is included", amount:0, span:'left', button:'Out of Stock'}
            ]
    }
  }
}
</script>

<style scoped>
@media (max-width:768px){
  *{
    margin:0;
    padding:0;
}  
}
main{
    width:67%;
    border:1px solid white;
    box-shadow:0px 0px 10px grey;
    margin-top:1rem;
    background: #fff;
}
@media (max-width:768px){
    main{
        width:90%;
    }
}
.header{
 padding-left:2.5rem;
 padding-right:3rem;
 margin-bottom:2rem;
}
@media (max-width:768px){
    .header{
        padding-left:1rem;
        padding-right:1rem;
    }
}
h1{
    font-size:16px;
    padding-top:1.5rem;
}
h2{
    font-size:16px;
    padding-top:1rem;
}
h3{
    font-size:16px;
    padding-top:1rem; 
    color:hsl(176, 50%, 47%);
}
@media (max-width:768px){
   h3{
      padding-top:0;  
    }
}
.header p {
    font-size:14px;
    padding-top:1rem;
    color:hsl(0, 0%, 48%);
}
.title{
    display:flex;
    justify-content: space-between;
}
@media (max-width:768px){
    .title{
        flex-direction:column;
        gap:5px;
    }
}
#details{
    width:76%;
    border:1px solid grey;
    margin-left:2.7rem;
    padding-left:1.5rem;
    margin-bottom:2rem;
    padding-right:2rem;
    background: #fff;
}
@media (max-width:768px){
    #details{
        margin-left:1.8rem;
        padding-right:0.5rem;
        width:70%;
    }
}
#details p{
    font-size:14px;
    color:hsl(0, 0%, 48%);
}
@media (max-width:768px){
    #details p{
        padding-top:1rem;
       
    }
}
.amount-section{
    display: flex;
    justify-content: space-between;
    margin-bottom:2rem;
    margin-top:2rem;
}
@media (max-width:768px){
    .amount-section{
        flex-direction:column;
        gap:10px;
        align-items:flex-start;
    }
}
button{
    padding-top:8px;
    padding-bottom:8px;
    padding-right:16px;
    padding-left:16px;
    border-radius:8px;
    border:none;
    background: hsl(176, 50%, 47%);
    color:#fff;
}
@media (max-width:768px){
    button{
        border-radius:16px;
    }
}
.details{
    opacity:0.5;
}
span{
    font-weight: 400;
    color:hsl(0, 0%, 48%);
}
</style>