<template>
  <!---html-->
  <div>
    How many people are there?<br>
    <input v-model="num" /><br>
    What's the age of the youngest person?<br>
    <input v-model="age" /><br>
    <button @click="groundturtle2">Get the age of all the students</button><br>
    <input v-model="a" /><br>
    <button @click="showFib(a)">Get a fibonacci</button>
    <button @click="showFact(a)">Get a factorial</button>
    <button @click="add">Get a timeout</button>
    <button @click="stop">Stop the timeout</button>
  </div>
</template>

<script>
//js

export default {
  name: "App", //页面名称
  components: {
    //导入vue的元素

  },
  data: () => ({
    //数据
    num: null,
    age: null,
    a:null,
    number: 1,
    myVar: null,
  }),
  methods:{
    groundturtle(){
      var i;
      var b = ['st','nd','rd','th','th','th','th','th','th']
      for (i = 1; i <= this.num; i++) {
        var a = Number(this.age)+(2*i)-2
        if((i==11)||(i==12)||(i==13)){
          window.alert('The '+i+b[3]+ ' person is '+ a + ' years old')
        }
        else if(i%10==0){
          window.alert('The '+i+b[b.length-1]+ ' person is '+ a + ' years old')
        }
        else{
          window.alert('The '+i+b[(i%10)-1]+ ' person is '+ a + ' years old')
        }
      }
    },
    fib: function(n){
      if(n==0||n==1){
        return 1
      }
      else{
        return this.fib(n-1)+this.fib(n-2)
      }
    },
    showFib(n){
      window.alert(this.fib(n))
    },
    factorial: function(n){
      if(n==1){
        return 1
      }
      return n*this.factorial(n-1)
    },
    showFact(n){
      window.alert(this.factorial(n))
    },
    add: function(){
      this.number++
      alert(this.number)
      this.myVar = setTimeout(this.add,2000)
    },
    stop: function(){
      clearTimeout(this.myVar)
    }

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
