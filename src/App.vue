<template>
  <div class="overlay" v-if="menuOpen"></div>
  <header>
    <nav>
      <div class="logo"><img src="./assets/logo.svg" alt=""></div>
      <div class="nav-links">
        <div class="hamburger" @click="menuOpen = !menuOpen">
          <img v-if="!menuOpen" src="./assets/icon-hamburger.svg" alt="">
          <img v-if="menuOpen" src="./assets/icon-close-menu.svg" alt="">
        </div>
        <div class="links" :class="menuOpen && 'show'">
          <div><a href="#">About</a></div>
          <div><a href="#">Discover</a></div>
          <div><a href="#">Get Started</a></div>
        </div>
      </div>
    </nav>
  </header>
  <main>
    <div>
      <section id="intro">
        <div class="logo"><img src="./assets/logo-mastercraft.svg" alt=""></div>
        <h2>Mastercraft Bamboo Monitor Riser</h2>
        <p>A beautiful & handcrafted monitor stand to reduce neck and eye strain.</p>
        <div class="buttons">
          <button class="btn" @click="state='pledgeModal'">Back this project</button>
          <button class="btn" id="bookmark" @click="bookmarked = !bookmarked">
            <div class="bookmark-icon">
              <img v-if="!bookmarked" src="./assets/icon-bookmark.svg" alt="">
              <img v-else src="./assets/icon-bookmarked.svg" alt="">
            </div>
            <span :class="bookmarked && 'bookmarked'">Bookmark<span v-if="bookmarked">ed</span></span>
          </button>
        </div>
      </section>
      <section id="stats">
        <div class="stats">
          <div class="stat">
            <div class="num">${{sum.toLocaleString("en-US")}}</div>
            <div>of $100,000 backed</div>
          </div>
          <div class="stat">
            <div class="num">{{backers.toLocaleString("en-US")}}</div>
            <div>total backers</div>
          </div>
          <div class="stat">
            <div class="num">56</div>
            <div>days left</div>
          </div>
        </div>
        <div class="progress-bar">
          <div class="progress" :style="{width:progress}"></div>
        </div>
      </section>

      <section id="about">
        <h3>About this project</h3>
        <p>
          The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform that elevates your screen 
          to a more comfortable viewing height. Placing your monitor at eye level has the potential to improve 
          your posture and make you more comfortable while at work, helping you stay focused on the task at hand.
        </p>
        <p>
          Featuring artisan craftsmanship, the simplicity of design creates extra desk space below your computer 
          to allow notepads, pens, and USB sticks to be stored under the stand.
        </p>
        <ProductCard :pledge="25" :remaining="101">
          <template v-slot:title>Black Edition Stand</template>
          <template v-slot:descr>
            You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you’ll be added to a special Backer member list.
          </template>
        </ProductCard>
        <ProductCard :pledge="75" :remaining="64">
          <template v-slot:title>Bamboo Stand</template>
          <template v-slot:descr>
            You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer member list. Shipping is included.
          </template>
        </ProductCard>
        <ProductCard class="out-of-stock" :pledge="25" :remaining="0">
          <template v-slot:title>Mahogany Special Edition</template>
          <template v-slot:descr>
            You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added to our Backer member list. Shipping is included.
          </template>
          <template v-slot:button>Out of Stock</template>
        </ProductCard>
      </section>
    </div>
  </main>
  <div class="modal" v-if=" state == 'pledgeModal'">
    <div class="modal-content">
      <div>
        <h3>Back this project</h3>
        <div class="close-modal" @click="state = 'main'">
          <svg width="14" height="15" xmlns="http://www.w3.org/2000/svg"><g fill="#7a7a7a" fill-rule="evenodd"><path d="M2.404.782l11.314 11.314-2.122 2.122L.282 2.904z"/><path d="M.282 12.096L11.596.782l2.122 2.122L2.404 14.218z"/></g></svg>
        </div>
      </div>
      
      <PledgeCard />
      <PledgeCard />
      <PledgeCard />
      <PledgeCard />
    </div>
  </div>
</template>

<script>
import ProductCard from './components/ProductCard.vue';
import PledgeCard from './components/Pledge.vue'
export default {
    name: "App",
    components:{
    ProductCard,
    PledgeCard,
},
    data() {
        return {
            menuOpen: false,
            bookmarked: false,
            sum: 89914,
            backers: 5007,
            target: 100000,
            state:"main",
        };
    },
    computed: {
        progress() {
            const result = (this.sum / this.target) * 100;
            return `${result}%`;
        }
    },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@400;500;700&display=swap');

:root{
--mod-cyan: #3cb4ac;
--dark-cyan: #147b74;
--black: hsl(0, 0%, 0%);
--dark-gray: #7a7a7a;
--gray:#FAFAFA;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Commissioner', sans-serif;
}

body{
  background-color: var(--gray);
  color:var(--dark-gray);
  font-size:14px;
}

a{
  text-decoration: none;
  color:inherit;
}

.btn{
  border:0;
  background-color: var(--mod-cyan);
  color:#fff;
  padding:1rem 1.6rem;
  border-radius: 1.5rem;
  font-weight: 700;
  cursor:pointer;
}

.btn:hover{
  background-color: var(--dark-cyan);
}

header{
  min-height: 260px;
  background-image: url("./assets/image-hero-mobile.jpg");
  padding:1.5rem;
  background-size: cover;
}

nav{
  display:flex;
  justify-content: space-between;
  position: relative;
  z-index: 50;
}


.overlay, .modal {
    display: block;
    position: fixed;
    top: 0;
    width: 100%;
    bottom: 0;
    pointer-events: none;
    background-color: rgba(0, 0, 0, 0.25);
    z-index: 1;
}

.modal{
  pointer-events: all;
}

.modal-content{
  background-color: #fff;
  margin:0 auto;
  margin-top:20%;
  width:90%;
  max-width: 500px;
  border-radius: 0.6rem;
  padding:1.3rem;
  height: 80vh;
  overflow: scroll;
}

.modal-content >div{
  display: flex;
  justify-content: space-between;
  margin:1rem 0 1.5rem 0;
}

.modal-content>div> h3{
  color:var(--black)
}

.links{
  display: none;
  width:100%;
  position: absolute;
  left:0;
  top:3rem;
  background-color: #fff;
  border-radius: 0.6rem;
  z-index: 100;
}

.links > div{
  padding:1.3rem;
}

.links > div:not(:last-of-type){
  border-bottom: 0.03rem solid var(--dark-gray);
}

.show{
  display:block;
}

main > div {
  width:90%;
  max-width: 500px;
  margin:0 auto;
  position: relative;
  top:-3rem;
}

section{
  background-color: #fff;
  text-align: center;
  padding:2rem 2rem;
  border-radius: 0.6rem;
  margin-bottom: 1.5rem;
}

#intro{
  position: relative;
  padding:2rem 1rem;
}

#intro > h2{
  color:var(--black);
}

#intro > p{
  font-size: 14px;
}

#intro > *{
  margin:1rem 0;
  line-height: 1.8rem;
}

 #intro> .logo {
  position:absolute;
  left:50%;
  top:0;
  transform: translate(-50%, -50%);
}

.buttons {
  margin-top: 2rem !important;
  display: flex;
  justify-content: space-between;
}

#bookmark{
  background-color: var(--gray);
  color:var(--dark-gray);
  position: relative;
  padding-left: 2rem;
}

#bookmark > span{
  display: none;
}

.bookmarked{
  color:var(--dark-cyan);
}

#bookmark > .bookmark-icon{
  position: absolute;
  left:-1.5rem;
  top:0;
}
#bookmark > .bookmark-icon > img{
  width:48px;
  height:48px;
}

.stats{
  font-size:13px;
}

.num{
  font-weight: 700;
  color:var(--black);
  font-size: 1.5rem;
}

.stat > div:not(.num){
  padding: 0.8rem 0;
}

.stat{
  margin-bottom:1.3rem;
}

.stat:not(:last-of-type){
  border-bottom: 0.1rem solid var(--gray);
  
}

.progress-bar{
  width:100%;
  background-color: var(--gray);
  height: 0.8rem;
  border-radius: 10px;
  overflow: hidden;
}

.progress{
  background-color: var(--mod-cyan);
  width:50%;
  height: 100%;
}

#about {
  text-align: left;
}

#about h3{
  color:var(--black);
}

#about> p{
  padding-top:1.8rem;
  font-size: 14px;
  line-height:1.6rem;
}

#about > p:last-of-type{
  margin-bottom: 1.8rem;
}

.out-of-stock{
  opacity:0.5;
}

.out-of-stock button{
  background-color: var(--dark-gray);
}

.modal{
  display: fixed;
  top:0;
  left:0;
}

@media (min-width:1025px){
  #app > .overlay{
    display: none;
  }
  header{
    background-image: url("./assets/image-hero-desktop.jpg");
    padding:2.6rem 6rem;
    height:320px;
  }
  .nav-links{
    display:flex;
    justify-content: space-between;
  }
  .hamburger{
    display: none;
  }

  .links{
    display:flex;
    color:#fff;
    position:static;
    background-color: transparent;
    border-radius: none;
  }

  .links > div{
    padding:0;
  }
  .links > div:not(:last-of-type){
    border-bottom: 0;
    margin-right: 1.2rem;
  }

  main >div, .modal-content{
    width:50%;
    max-width: 800px;
  }

   .modal-content{
    margin-top:8%;
   }

  .buttons {
    padding-left: 2rem;
    padding-right: 2rem;
  }

  #bookmark > span{
    display: inline;
  }

  #stats{
    padding:2rem 3rem;
  }

  .stats{
    display: flex;
    justify-content: space-between;
    text-align: left;
  }

  .stat{
    padding-left:0;
  }

  .stat:not(:last-of-type){
    border-bottom: none;
    border-right: 0.15rem solid var(--gray);
    width:33.33%;
}

}

</style>
