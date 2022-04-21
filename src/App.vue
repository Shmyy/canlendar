<template>
  <div id="app">
    <div class="left">
      <heads></heads>
      <bodys></bodys>
    </div>
    <div class="right">
      <detail></detail>
    </div>
  </div>
</template>

<script>
import heads from './components/head.vue'
import bodys from './components/bodys'
import detail from './components/detail'

export default {
  name: 'App',
  components: {
    heads,
    bodys,
    detail
  }
}
</script>

<style>
#app{
  display: flex;
  flex-direction: row;

  width: 600px;
  height: 500px;
  margin: 100px auto;
  /* background-color: red; */
  border:solid 1px  black;
}

.left{
  display: flex;
  flex-direction: column;
  
  flex: 3;
  height: 500px;
  /* background-color: aqua; */
}
.right{
  display: flex;
  flex: 1;

  height: 500px;
  /* background-color: orange; */
}
</style>
