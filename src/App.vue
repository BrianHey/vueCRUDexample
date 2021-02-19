<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <HelloWorld msg="Majin Boo" /> -->
    <Jugadores  />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Jugadores from "./components/Jugadores.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    Jugadores,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
