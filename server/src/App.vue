<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view/> -->
     <!-- 注文一覧のOrdersコンポーネント -->
  <Orders></Orders>

  </div>
</template>

<script>
/* eslint-disable*/
import ViewList from "./components/OrderList.vue";
export default {
  name: 'App',
   components: {
    Orders: ViewList,
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
