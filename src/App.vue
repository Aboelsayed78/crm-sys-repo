<template>
  <div id="app">
    <SideBar />
    <MainPage />
    <div class="clear"></div>
  </div>
</template>

<script>
import SideBar from "./components/SideBar.vue";
import MainPage from "./components/MainPage.vue";
export default {
  name: "App",
  props: {},
  components: {
    SideBar,
    MainPage,
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
  overflow: hidden;
}
</style>
