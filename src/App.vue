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
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data(){
    return{
      menuOpen:false,
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@400;500;700&display=swap');

:root{
--mod-cyan: hsl(176, 50%, 47%);
--dark-cyan: hsl(176, 72%, 28%);
--black: hsl(0, 0%, 0%);
--dark-gray: hsl(0, 0%, 48%);
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Commissioner', sans-serif;
}

a{
  text-decoration: none;
  color:inherit;
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

@media (min-width:1025px){
  header{
    background-image: url("./assets/image-hero-desktop.jpg");
    padding:2.6rem 4rem;
    height:350px;
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
}

</style>
