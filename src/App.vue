<template>
  <!---html-->
  <div>
    <!-- <Extra1 /> -->
    <!-- <Extra2 /> -->
    <!-- <Extra3 /> -->
    <Alarm v-for="(i,index) in id" :key="index" :id=i />
    <!-- <Home /> -->
    <Animation />
    <Calculator2 />
    <!-- <basic-js/> -->
    <!-- <Number /> -->
    <!-- <Date /> -->
    <!-- <JSON /> -->
    <!-- <Vue />
    <WatchPractice /> -->
    <!-- <Todo /> -->
    <!-- <Father />
    <Tabs /> -->
    
  </div>
</template>

<script>
//js
// import Extra1 from "./components/Extra1.vue";
// import Extra2 from "./components/Extra2.vue";
import Alarm from "./components/Alarm.vue";
// import BasicJs from "./components/BasicJs.vue";
// import Number from "./components/Number.vue";
// import Date from "./components/Date.vue";
// import JSON from "./components/JSON.vue";
// import Vue from "./components/Vue.vue";
// import WatchPractice from "./components/WatchPractice.vue";
// import Extra3 from "./components/Extra3.vue";
// import Todo from "./components/Todo.vue";
// import Father from "./components/Father.vue";
// import Tabs from "./components/Tabs.vue";
import Animation from "./components/Animation.vue";
// import Home from "./components/Home.vue";
import Calculator2 from "./components/Calculator2.vue";


export default {
  name: "App", //页面名称
  components: {
    //导入vue的元素
    // Extra1,
    // Extra2,
    // Extra3,
    Alarm,
    // BasicJs,
    // Number,
    // Date,
    // JSON,
    // Vue,
    // WatchPractice,
    // Todo,
    // Father,
    // Tabs,
    Animation,
    // Home,
    Calculator2,
  },

  // 在渲染前，有数据后
  data: () => ({
    //数据
    id: [1],
  }),
  methods:{

  }
};
</script> 

<style>
/* css */
/* #app { 
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 100px;
} */
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
