<template>
  <!---html-->
  <div>
    This is the number {{id}} clock <br>
    <button @click="showTime">Change size and Show/Hide</button>
    <select size="1" @change="changeSize($event)" style="height: 50px;">
      <option v-for="(todo,i) in todos[id%4-1]" :key="i" :value="i">{{todo}}</option>
    </select>
    <audio ref="audioalarm">
      <source src="assets/sound/alarm.mp3" type="audio/mp3" />
    </audio>
    <!-- <Extra1 /> -->
    <p v-if="seen%4==0"><strong>{{hours}}:{{minutes}}:{{seconds}} {{ampm}}</strong></p>
    <p v-else-if="seen%4==1">{{hours}}:{{minutes}}:{{seconds}} {{ampm}}</p>
    <div v-else-if="seen%4==2"><strong>{{hours}}:{{minutes}}:{{seconds}} {{ampm}}</strong></div>
    <div v-else></div>

  </div>

</template>

<script>
//js
// import Extra1 from "./components/Extra1.vue";


export default {
  props:{
    id: undefined,
  },
  name: "App", //页面名称
  components: {
    //导入vue的元素
    // Extra1,
  },

  // 在渲染前，有数据后
  mounted(){
    this.showtime()
    this.setAlarm()
    this.seen = this.id-1
  },
  data: () => ({
    //数据
    hours:'00',
    minutes:'00',
    seconds:'00',
    ampm: '00',
    alarm:{
      hr: '13',
      mts: '00',
      ssecs: '00',
      am_pm: 'pm',
    },
    message: 'Class is over',
    seen: 0,
    todos1: ['Large','Medium','Small','Hide'],
    todos2: ['Medium','Small','Hide','Large'],
    todos3: ['Small','Hide','Large','Medium'],
    todos4: ['Hide','Large','Medium','Small'],
    todos:[['Large','Medium','Small','Hide'],['Medium','Small','Hide','Large'],['Small','Hide','Large','Medium'],['Hide','Large','Medium','Small']]
  }),
  methods:{
    playmusic(){
      var vm = this;
      var playPromise = vm.$refs.audioalarm.play();
      if (playPromise != undefined){
        playPromise.then(a => {
          console.log(a)
          vm.$refs.audioalarm.pause()
        })
      }
    },
    showTime: function(){
      this.seen +=1
      console.log(this.seen)
    },
    changeSize: function(event){
      this.seen = Number(event.target.value)
    },
    setAlarm() {
      var vm = this;
      var hrs = vm.alarm.hr;
      var min = vm.alarm.mts;
      var sec = vm.alarm.ssecs;
      var apm = vm.alarm.am_pm;
      if ((vm.hours == hrs) &&
         (vm.minutes == min) &&
         (vm.seconds == sec) &&
         (vm.ampm == apm)) {
        vm.playmusic()
        if (vm.message) {
          window.alert(vm.message);
        }
        return false}
      if (hrs == '') {alert('The Hour field is empty.'); return false}
      if (min == '') {alert('The Minute field is empty.'); return false}
      if (apm == '') {alert('The am/pm field is empty.'); return false}
      if (hrs.length == 1) {vm.alarm.hr = '0' + hrs}
      if (min.length == 1) {vm.alarm.mts = '0' + min}
      if (sec.length == 1) {vm.alarm.mts = '0' + min}
      if (hrs.length > 2) {alert('The Hour is entered wrong.'); return false}
      if (min.length > 2) {alert('The Minute is entered wrong.'); return false}
      if (sec.length > 2) {alert('The Second is entered wrong.'); return false}
      if (apm != 'am' && apm != 'pm' ) {alert('The am/pm is entered wrong.'); return false}
      setTimeout(vm.setAlarm, 1000);
    },
    showtime() {
      var vm = this;
      var now=new Date();
      var hour=now.getHours();
      var min=now.getMinutes();
      var sec=now.getSeconds();
      var add = null;
      if (min<=9) {
        min="0"+min;
      }
      if (sec<=9) {
        sec="0"+sec;
      }
      if (hour>=12) {
        add="pm";
      }
      else {
        // hour=hour;
        add="am";
      }
      vm.hours = (hour<=9) ? "0"+hour : hour;
      vm.minutes = min;
      vm.seconds = sec;
      vm.ampm= add;
      setTimeout(vm.showtime, 1000);
    }
  }
};
</script> 

<style scoped>
/* css */
/* #app { 
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 100px;
} */
p {
  margin-top: 20%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: crimson;
  font-size: 100px;
}
</style>
