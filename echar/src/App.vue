<template>
  <div id="app">
    <Pipe></Pipe>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <shuidi></shuidi>
    <Guanxi></Guanxi>
    <Jianzhui></Jianzhui>
    <Liti></Liti>
    <Leida></Leida>
    <Fengezhuxingtu></Fengezhuxingtu>
    <Tupu></Tupu>
    <Yibiaopan></Yibiaopan>
    <Litiyuanzhu></Litiyuanzhu>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'
  import Pipe from "./components/Pipe";
  import Shuidi from "./components/Shuidi";
  import Guanxi from "./components/Guanxi";
  import Jianzhui from "./components/Jianzhuizhuxingtu";
  import Liti from "./components/Litizhuzhuangtu";
  import Leida from "./components/Leida";
  import Fengezhuxingtu from "./components/Fengezhuxingtu";
  import Tupu from "./components/Tupu";
  import Yibiaopan from "./components/Yibiaopan";
  import Litiyuanzhu from "./components/Litiyuanzhu";
  export default {
    name: 'App',
    components: {
      Pipe,
      HelloWorld,
      Shuidi,
      Guanxi,
      Jianzhui,
      Liti,
      Leida,
      Fengezhuxingtu,
      Tupu,
      Yibiaopan,
      Litiyuanzhu,
    }
  }
</script>

<style scoped>
#app{
  display: flex;
  flex-wrap: wrap;
}
</style>
