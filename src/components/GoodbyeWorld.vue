<template>
  <p>{{message}}</p>
  <button v-on:click="reverseMessage">反转消息</button>
  <p>{{input1}}</p>
  <input v-model="input1" />
  <br>
  <input v-model="input1" />
  <!-- v-model  双向绑定, similar to what happens when you don't .copy()-->
  <br>
  <span v-once>{{input1}}</span> 
  <!-- v-once cannot be changed -->
</template> 

<script>
export default {
  props: ["message"],
  methods: {
    reverseMessage: function () {
      this.input1 = this.input1.split("").reverse().join("");
    //   'this' means this program's memory address
    },
  },
  data: () => ({
    input1: 'Type!',
  }),
};
</script>
