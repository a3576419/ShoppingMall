<template>
  <div id="app">
    <div id="nav">
      <router-link to="/"></router-link>
    </div>
    <router-view/>
      <main-tab-bar></main-tab-bar>
  </div>
</template>

<script>
    import MainTabBar from "@/components/content/mainTabbar/MainTabBar";
    export default {
        name: "App",
        components: {MainTabBar}
    }
</script>
<style>
    @import "assets/css/base.css";

</style>
