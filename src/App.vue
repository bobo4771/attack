<template>
  <div id="app">
    <HelloWorld msg="" />
    <img src="./assets/e.gif" width="400" height="200" />
    <battle label />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import battle from "./components/battle.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    battle,
  },

  data: function () {
    return {};
  },

  methods: {},
};
</script>

<style>
#app {
  font-family: "Metal Mania", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #16ff3d;
  margin-top: 60px;
}
body {
  background-image: url(./assets/bg2.gif);
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
</style>
