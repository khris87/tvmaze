<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div class="container"><TvMaze /></div>

    <HelloWorld msg="Welcome to Your Vue.js App to implemente tvMaze API"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import TvMaze from "../components/TvMaze";

export default {
  name: 'home',
  components: {
    TvMaze,
    HelloWorld
  }

}
</script>
