<template>
  <div>
    <header>
          <sidebar-section v-if="showSidebar"/>
        <nav>
            <ul>
                <img src="@/assets/images/logo.svg" alt="nav-logo" id="nav-logo">
            </ul>
            <ul>
               <icon-section :showIcon="showIcon" :toggleSidebar="toggleSidebar" />
                <li>About</li>
                <li>Discover</li>
                <li>Get Started</li>
            </ul>
        </nav>
    </header>
     <main>
        <project-section :showProject="showProject" :closePage="closePage"/>
    <section>
        <img src="@/assets/images/logo-mastercraft.svg" alt="logo-mastercraft" id="logo-mastercraft">
        <h1>Mastercraft Bamboo Monitor Riser</h1>
        <p>A beautiful bandcrafted monitor stand to reduce neck and eye strain</p>
        <div> 
            <button id="btn-project" @click="displayProject">Back this project</button>
            <button id="btn-bookmark" @click="toggleBookmark"  :class="{ 'reversed': clicked }" >
                <img src="@/assets/images/icon-bookmark.svg" alt="icon-bookmark" id="icon-bookmark">
                <p>Bookmark</p>
            </button>
        </div>
    </section>
    <div id="pledge-section">
        <div id="pledge-details">
            <p><strong>${{deposit}}</strong>  <br><span>of ${{total}} backed</span></p>
            <p><strong>5,007</strong> <br><span>total backers</span></p>
            <p><strong>56</strong> <br><span>days left</span></p>
        </div>
        <div id="pledge-container">
            <div v-bind:style="{ width: progressPercentage + '%' }"></div>
        </div>
    </div>
    <about-section/>
    </main>
  </div>
</template>

<script>
import AboutSection from '@/components/AboutSection.vue';
import ProjectSection from '@/components/ProjectSection.vue';
import IconSection from '@/components/IconSection.vue';
import SidebarSection from '@/components/SidebarSection.vue';
export default {
  components: {
   AboutSection,
   ProjectSection,
   IconSection,
   SidebarSection
  },
  data(){
   return{
        showProject:false,
        deposit:89914,
        total:100000,
        clicked:false,
        showIcon:false,
        showSidebar:false
    }
  },
  methods:{
    displayProject(){
    this.showProject =! this.showProject;
    },
    closePage(){
     this.showProject = false;
    },
    toggleBookmark(){
        this.clicked =! this.clicked;
    },
    toggleSidebar(){
        this.showSidebar =  !this.showSidebar;
    }
  },
  computed:{
    progressPercentage(){
    return  (this.deposit / this.total) * 100 ;
    }
  },
  mounted(){
    if(window.innerWidth <= 768){
        this.showIcon =! this.showIcon;
    }
  }
}
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@400;500;700&family=DM+Sans:opsz,wght@9..40,400;9..40,500&family=Inter&family=Josefin+Sans:wght@400;700&family=Karla:wght@400;700&family=Kumbh+Sans:wght@400;700&family=League+Spartan:wght@500;700&family=Lexend+Deca&family=Manrope:wght@800&family=Plus+Jakarta+Sans:wght@500;800&family=Roboto:wght@400;700&display=swap');
 div{
    font-family:Commissioner;
 }
 header{
    position:absolute;
    top:8px;
    left:120px;
 }
 @media(max-width:768px){
    header{
        position:absolute;
        left:-16px;
        top:-8px;
    }
 }
 nav{
    display:flex;
    gap:34rem;  
 }
 @media (max-width:768px){
    nav{
        gap:0;
    }
 }
 ul{
    display:flex;
    gap:30px;
 }
 li{
    list-style-type: none;
    color:#fff;
 }
 @media(max-width:768px){
    li{
        display:none;
    }
 }
main{
    position:absolute;
    left:375px;
    top:270px;
    z-index:5;
}
@media(max-width:768px){
    main{
        position:absolute;
        left:30px;
        top:110px;
    }
}
section{
    border:1px solid #fff;
    box-shadow: 0px 0px 10px rgb(235, 235, 235);
    width:67%;
    background:#fff;
}
@media(max-width:768px){
    section{
        width:90%;
    }
}
#logo-mastercraft{
 position: absolute;
 top:-18px;
 left:310px;
 width:36px;
}
@media(max-width:768px){
    #logo-mastercraft{
        position:absolute;
        left:140px;
    }
}
h1{
     text-align: center;
     padding-top:12px;
}
section p {
    text-align: center;
    color:hsl(0, 0%, 48%);
}
section div{
    display:flex;
    align-items: center;
    justify-content:space-between;
}
#btn-bookmark{
    display:flex;
    gap:0.5rem;
    justify-content: flex-end;
    align-items: center;
    margin-right:2.5rem;
    border-radius:1.5rem;
    border:none;
    padding-right:0;
    padding-left:2px;
    background:#ebeaea;
    margin-bottom:2rem;
    margin-top:0.8rem;
    cursor:pointer;
    outline:none;
}
@media (max-width:768px){
    #btn-bookmark{
        margin-right:1.5rem;
    }
}
#btn-bookmark p {
    padding-right:12px;
}
#btn-project{
    padding-top:14px;
    padding-bottom:14px;
    padding-left:22px;
    padding-right:22px;
    color:#fff;
    background:hsl(176, 50%, 47%);
    border:none;
    margin-left:2.5rem;
    margin-top:0.8rem;
    border-radius:1.5rem;
    margin-bottom:2rem;
    cursor:pointer;
}
@media (max-width:768px){
    #btn-project{
        padding-left:16px;
        padding-right:16px;
        margin-left:1.5rem;
    }
}
#icon-bookmark{
    width:40px;
    margin:0;
   
}
#pledge-section{
    border:1px solid #fff;
    box-shadow: 0px 0px 10px rgb(226, 225, 225);
    width:67%;
    margin-top:1rem;
}
@media(max-width:768px){
    #pledge-section{
        width:90%;
    }
}
#pledge-details{
    display:flex;
    gap:3rem;
    padding-left:4rem;
    padding-right:3rem;
    padding-top:1.5rem;
}
#pledge-details p:not(:last-child){
    content:"";
    padding-right:2rem;
    border-right:1px solid rgb(214, 212, 212);
}
@media (max-width:768px){
    #pledge-details p:not(:last-child){
        border-right:none;
        border-bottom: 1px solid rgb(214, 212, 212);
        padding-bottom:2.5rem;
    }
}
@media (max-width:768px){
    #pledge-details{
        flex-direction:column;
        padding-left:0;
        padding-right:0;
        gap:0;
        align-items: center;
    }
}
strong{
    font-size:24px;
}
@media (max-width:768px){
    strong{
        font-size:29px;
    }
}
span{
    font-size:12px;
    color:hsl(0, 0%, 48%);
}
#pledge-container{
    width:85%;
    border:1px solid #fff;
    background: rgb(250, 247, 247);
    margin-bottom:2.5rem;
    margin-left:3rem;
    border-radius:0.5rem;
}
@media (max-width:768px){
    #pledge-container{
        margin-left:1.5rem;
    }
}
#pledge-container div{
    height:10px;
    background: hsl(176, 50%, 47%);
    border-radius:4px;
}
.reversed{
    flex-direction: row-reverse;
    background: hsl(176, 50%, 47%);
}
</style>
