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
