<template>
  <div class="hello">
    <h1>{{ msg }}</h1> <!--从外部(app.vue)导入数据-->
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
