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
            <button id="btn-bookmark" @click="toggleBookmark" :class="{'reserved': clicked}">
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
    box-shadow: 0px 0px 10px grey;
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
    align-items: center;
    margin-right:1.5rem;
    border-radius:1rem;
    border:none;
    padding-left:16px;
    padding-right:16px;
    background:#fff;
    margin-bottom:1rem;
}
#btn-project{
    padding-top:10px;
    padding-bottom:10px;
    padding-left:20px;
    padding-right:20px;
    color:#fff;
    background:hsl(176, 50%, 47%);
    border:none;
    margin-left:1.5rem;
    border-radius:1rem;
    margin-bottom:1rem;
}
#icon-bookmark{
    width:24px;
}
#pledge-section{
    border:1px solid #fff;
    box-shadow: 0px 0px 10px grey;
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
    gap:6rem;
    padding-left:2rem;
    padding-right:3rem;
}
@media (max-width:768px){
    #pledge-details{
        flex-direction:column;
        padding-left:0;
        padding-right:0;
        gap:1rem;
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
    margin-bottom:1rem;
    margin-left:2.2rem;
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
.reserved{
    flex-direction: row-reverse;
    color:hsl(176, 50%, 47%);
}

/* #nav-logo{
    width:128px;
}
@media(max-width){
    #nav-logo{
        width:5px;
        height: 2px;
    
    }
} */
</style>
