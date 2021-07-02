<template>
  <div id="app">
    <Pipe></Pipe>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Shuidi></Shuidi>
    <Guanxi></Guanxi>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Pipe from "./components/Pipe";
import Shuidi from "./components/Shuidi";
import Guanxi from "./components/Guanxi";

export default {
  name: 'App',
  components: {
    Pipe,
    HelloWorld,
    Shuidi,
    Guanxi,
  }
}
</script>

<style>

</style>
