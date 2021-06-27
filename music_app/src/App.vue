<template>
  <div class="topBar">
    <AnimeQuote/> 
  </div>
  <img alt="logo" src="./assets/musicLogo.svg">
  <MusicList/>
</template>

<script>

import MusicList from "./components/MusicList"
import AnimeQuote from "./components/AnimeQuote.vue"

export default {
  name: 'App',
  components: {
    MusicList,
    AnimeQuote
  }
}


</script>

<style>

@font-face {
  font-family: "Lobster";
  src: local("Lobster"),
   url(./fonts/Lobster-Regular.ttf) format("truetype");
}

@font-face {
  font-family: "LibreFranklin-Italic";
  src: local("LibreFranklin-Italic"),
   url(./fonts/LibreFranklin-Italic.ttf) format("truetype");
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(225, 225, 225);
  margin: 0;
}

body {
  background-color: rgb(15, 15, 15);
  margin: 0;
}

.topBar {
  width: 100%;
  height: auto;
  background-color: salmon;
  background: rgb(0,254,255);
  background: linear-gradient(135deg, rgba(0,254,255,1) 0%, rgba(139,55,228,1) 50%, rgba(200,0,199,1) 100%);
}

img {
  margin-top: 1em;
  height: 15vw;
}


</style>
