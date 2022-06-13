<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question" />
    </p>
    <p>{{ answer }}</p>
    <img :src="imgsrc" />
  </div>
</template>



<script>
// the 2 scripts above is similar to import
// Axios 可以和API建立连接
import axios from "axios";
import _ from "lodash";

export default {
  data: () => ({
    question: "",
    answer: "I cannot give you an answer until you ask a question!",
    imgsrc: undefined,
  }),
  watch: {
    // 如果 'question' 发生改变，这个函数就会运行
    question: function () {
      this.answer = "Waiting for you to stop typing...";
      this.debouncedGetAnswer();
    },
  },
  // created 是页面加载的情况下
  created: function () {
    // `_.debounce` 是一个通过 Lodash 限制操作频率的函数。
    // 在这个例子中，我们希望限制访问 yesno.wtf/api 的频率
    // AJAX 请求直到用户输入完毕才会发出。想要了解更多关于
    // `_.debounce` 函数 (及其近亲 `_.throttle`) 的知识，
    // 请参考：https://lodash.com/docs#debounce
    this.debouncedGetAnswer = _.debounce(this.getAnswer, 500);
  },
  methods: {
    getAnswer: function () {
      if (
        this.question.indexOf("?") === -1 &&
        this.question.indexOf("？") === -1
      ) {
        this.answer = "Questions usually contain a question mark. ;-)";
        this.imgsrc = undefined;
        return;
      }
      this.answer = "Thinking...";
      var vm = this;
      //顺序是get = axios.get, get.then, get.then.catch
      axios
        .get("https://yesno.wtf/api")
        .then(function (response) {
          vm.answer = _.capitalize(response.data.answer);
          vm.imgsrc = response.data.image;
        })
        .catch(function (error) {
          vm.answer = "Error! Could not reach the API. " + error;
        });
    },
  },
};
</script>