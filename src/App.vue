<template>
  <div id="app">
    <div class="jumbotron">
      <h1>TP4</h1>
      <br>
      <Navbar />
      <router-view></router-view>
    </div>

  </div>
</template>

<script>
import Navbar from "./componentes/Navbar.vue";

export default {
  name: "App",
  components: {
    Navbar
  },
};
</script>

<style>
#app {

}
</style>
