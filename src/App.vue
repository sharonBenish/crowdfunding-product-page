<template>
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
          <button class="btn">Back this project</button>
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
    </div>
  </main>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      menuOpen:false,
      bookmarked:false,
      sum:89914,
      backers:5007,
      target:100000,
    }
  },
  computed:{
    progress(){
      const result = (this.sum / this.target)*100;
      return `${result}%`
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@400;500;700&display=swap');

:root{
--mod-cyan: #3cb4ac;
--dark-cyan: #147b74;
--black: hsl(0, 0%, 0%);
--dark-gray: hsl(0, 0%, 48%);
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
  color:var(--dark-gray)
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
  padding:2rem 1rem;
  border-radius: 0.6rem;
  margin-bottom: 1.5rem;
}

#intro{
  position: relative;
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


@media (min-width:1025px){
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

  main >div{
    width:50%;
    max-width: 600px;
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
