<template>
  <div>
    <HelloWorld :msg="message2" />
    <span :title="message2" v-if="seen">{{message}}</span>
    <!-- v-if is just simply if,mostly used to display stuff or not -->
    <ol>
      <li v-for="(todo,i) in todos" :key="i">{{todo.text}}</li>
      <!-- v-for iterates all the elements and creates them in HTML, 
      v-for requires an index and we need a key to hold this-->
    </ol>
    <GoodbyeWorld :message="message" />
    <p>Using mustaches: {{rawHtml}}</p>
    <!-- {{}} is called mustache -->
    <p>
      Using v-html:
      <span v-html="rawHtml"></span>
    </p>
    <button @click="pie">Get a pie</button>
    <p>This is the original message: {{message}}</p>
    <p>This {{reverse}}</p>
    <p>
      <strong>{{pi}}</strong>
    </p>
    <p>{{floattostringreverse}}</p>
    <p>{{classover}}</p>
  </div>
</template>

<script>
import GoodbyeWorld from "./GoodbyeWorld.vue";
import HelloWorld from "./HelloWorld.vue";

export default {
  components: {
    HelloWorld,
    GoodbyeWorld,
  },
  computed: {
    reverse: function () {
      return this.message.split("").reverse().join("");
    },
    pi: function () {
      window.alert(Math.PI);
      return Math.PI;
    },
    floattostringreverse: function () {
      return Math.PI.toString().split("").reverse().join("");
    },
    classover: function () {
      return Date.now();
    },
  },
  data: () => ({
    message: "hellooooo worlddddddd",
    message2: "It's " + new Date().toLocaleString(), //时间
    seen: false,
    todos: [{ text: "A" }, { text: "B" }, { text: "C" }],
    rawHtml: '<span style="color:red"> This should be red. </span>',
  }),
  methods: {
    pie: function () {
      window.alert(Math.PI);
    },
  },
};
</script>

<!--shift option f to format code -->