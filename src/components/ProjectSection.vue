<template>
  <div v-if="showProject">
    <div class="overlay">
   <main>
    <header>
        <img src="@/assets/images/icon-close-modal.svg" alt="icon-close" @click="closePage">
        <h1>Back this project</h1>
    </header>
    <section>
        <h2>Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the world?</h2>
        <div class="pledge-reward">
            <h3>Pledge with no reward</h3>
            <p>Choose to support us without a reward if you simply believe in our project.As a backer,you will be signed up to receive product updates via email.</p>
        </div>
        <div id="details" v-for="detail in details"  :key="detail.id" :class="{'selected': isSelected === detail }"> 
            <div :class="{'details':detail.amount === 0}">
            <div class="label">
                <div class="input">
             <input type="radio" id="detail" name="detail" v-model="isSelected" @change="displaySection(detail)"/>
             <label for="details" >{{detail.label}}   <span>{{detail.pledge}}</span></label>
                </div>
             <p>{{detail.amount}} <span>{{detail.span}}</span></p>
            </div>
            <p id="content">{{detail.content}}</p>
             <p id="pledge-left">{{detail.amount}} <span>{{detail.span}}</span></p>
            <div class="pledge-section" v-if="isSelected === detail">
                <p>{{detail.pledgeEntry}}</p>
                <div class="btn-container"> 
                    <button id="btn-amount">{{detail.btnAmount}}</button>
                    <button id="btn-continue">{{detail.btnContinue}}</button>
                </div>
            </div>
            </div>
        </div>
    </section>
   </main>
   </div>
  </div>
</template>

<script>
export default {
  props: {
   showProject: Boolean,
   closePage: Function,

  },
  data() {
    return {
        details: [
            {id:1, label:'Bamboo Stand', pledge:'Pledge $25 or more', amount:'101', span:'left', content:"You get an ergonomic stand made of natural bamboo.You've helped us launch our promotional campaign,and you'll be added to a special Backer member list.", pledgeEntry:'Enter your pledge', btnAmount:'$25', btnContinue:'Continue'},
            {id:2, label:'Black Edition Stand',  pledge:'Pledge $75 or more', amount:'64', span:'left', content:"You get a Black Special Edition computer stand and a personal thank you.You'll be added to our Backer member list.Shopping is included.", pledgeEntry:'Enter your pledge', btnAmount:'$25', btnContinue:'Continue'},
            {id:3, label:'Mahogamy Special Edition', pledge:'Pledge $200 or more', amount:'0', span:'left', content:"You get two Special Edition Mahogany stands,a Backer T-Shirt and a personal thank you.You'll be added to our Backer member list.Shipping is included", pledgeEntry:'Enter your pledge', btnAmount:'$25', btnContinue:'Continue'}
        ],
        isSelected:false
        
    }
  },
  methods:{
    displaySection(detail){
      this.isSelected = detail;
    }
    }
  
}
</script>
<style scoped>
.overlay{
    position: fixed;
    top:0;
    left:0;
    width:100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}
main{
    width:50%;
    height:100%;
    border:1px solid #fff;
    border-radius:8px;
    background: #fff;
    z-index:1500;
    overflow-y: auto; 
    
}
@media (max-width:768px){
    main{
        width:70%;
    }
}
img{
   float:right;
   padding-right: 2rem;
   padding-top:0.5rem;
}
@media (max-width:768px){
    img{
        padding-right:10px;
        padding-top:0;
    }
}
@media (max-width:768px){
    header{
        display:flex;
        flex-direction: row-reverse;
        align-items:center;
        gap:2rem;
        justify-content: space-between;
        padding-top:1rem;
    }
}
h1{
    font-size: 22px;
    padding-left:2rem;
    padding-top:1rem;
}
@media (max-width:768px){
    h1{
        font-size:16px;
        padding-left:8px;
        padding-top:0;
    }
}
h2{
    font-size:15px;
    padding-left:1.7rem;
    font-weight: 400;
    color:hsl(0, 0%, 48%);
}
@media (max-width:768px){
    h2{
        padding-left:9px;
        font-size:12px;
        font-weight:normal;
    }
}
.pledge-reward{
    border:1px solid grey;
    width:90%;
    margin-left:auto;
    margin-right:auto;
    margin-top:2rem;
    margin-bottom:1.5rem;
}
@media (max-width:768px){
    .pledge-reward{
        border-radius:8px;
    }
}
h3{
    font-size:15px;
    padding-left:2rem;
}
@media (max-width:768px){
    h3{
        font-size:13px;
    }
}
.pledge-reward p{
    font-size:15px;
    padding-left:2rem;
    padding-bottom: 1rem;
    color:hsl(0, 0%, 48%);
}
@media (max-width:768px){
    .pledge-reward p{ 
        font-size:12px;
        padding-left:1.5rem;
        padding-right:1rem;
        padding-bottom:0.5rem;
    }
}
#details{
   width:90%;
   border:1px solid grey;
   margin-left:auto;
   margin-right:auto;
   margin-bottom:1.5rem;
   border-radius:8px;
}
.selected {
    border:1px solid hsl(176, 50%, 47%);
}
#content{
    font-size:15px;
    font-weight:400;
    padding-left:1rem;
    padding-right:1rem;
    padding-bottom:1rem;
    color:hsl(0, 0%, 48%);
}
@media (max-width:768px){
    #content{
        font-size:12px;
        padding-top:1.5rem;
    }
}
.input{
    display:flex;
    align-items: center;
    gap:10px;
}
@media (max-width:768px){
    .input{
        gap:12px;
    }
}
.label{
    display:flex;
    align-items: center;
    justify-content: space-between;
    padding-left:1rem;
    padding-right:1rem;
    padding-top:1rem;
    margin-bottom:-1rem;
}
.label p{
    font-size:15px;
    font-weight: 700;
}
@media (max-width:768px){
    .label p{
        display:none
    }
}
.label p span{
    font-weight:400;
    color:hsl(0, 0%, 48%);
}
label{
    font-size:15px;
    font-weight:700;
}
@media (max-width:768px){
    label{
        font-weight:700;
        font-size:13px;
        display:flex;
        flex-direction:column;
        gap:4px;
    }
}
label span{
    padding-left:8px;
    color:hsl(176, 50%, 47%);
}
@media(max-width:768px){
    label span{
       padding-left:0;
    }
}
.pledge-section{
    display:flex;
    align-items: center;
    justify-content: space-between;
    padding-left:1rem;
    padding-right:2rem;
    padding-bottom:1rem;
    padding-top:1.5rem;
    border-top:1px solid grey;
}
@media (max-width:768px){
    .pledge-section{
        flex-direction: column;
    }
}
@media (max-width:768px){
    .pledge-section p {
        font-size:12px;
    }
}
.btn-container{
    display:flex;
    gap:10px;
}
#btn-amount{
    padding-left:1rem;
    padding-right:1.5rem;
    padding-top:0.7rem;
    padding-bottom:0.7rem;
    border:none;
    border-radius:1rem;
    background: hsl(176, 50%, 47%);
    color:#fff;
}
@media (max-width:768px){
    #btn-amount{
        padding-left:1.2rem;
        padding-right:1.7rem;
        background:rgb(230, 228, 228);
        color:black;
        font-weight:700;
    }
}
#btn-continue{
    padding-left:1rem;
    padding-right:1rem;
    padding-top:0.7rem;
    padding-bottom:0.7rem;
    border:none;
    border-radius:1rem;
}
@media (max-width:768px){
    #btn-continue{
        color:#fff;
        background:hsl(176, 50%, 47%);
        border-radius:1rem;
    }
}
.details{
    opacity:0.5;
}
#pledge-left{
   display:none;
}
@media (max-width:768px){
    #pledge-left{
        margin-top:-1rem;
        display: block;
        padding-left:1rem;
        font-weight: 700;
    }
}
@media (max-width:769px){
    #pledge-left span{
        font-weight:400;
        color:hsl(0, 0%, 48%);
    }
}
</style>