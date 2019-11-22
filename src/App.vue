<template>
  <div id="app">
    <home-page />
  </div>
</template>

<script>

import HomePage from '@/components/HomePage'
export default {
  name: 'app',
  components: {
    HomePage
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
  width: 3840px;
  height: 1080px;
  margin: 0;
  padding: 0;
}

  html,body {
    width: 3840px;
    height: 1080px;
    margin: 0;
    padding: 0;
  }
</style>
