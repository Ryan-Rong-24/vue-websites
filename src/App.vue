<template> <!---html-->
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script> //js
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App', //页面名称
  components: { //导入vue的元素
    HelloWorld
  },
  data:()=>({ //数据

  })
}
</script> 

<style> 
/* css */ 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
