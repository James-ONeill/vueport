<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <PageScroll>
      <div class="scroll-progress-container" slot-scope="{ scrollPercentage }">
          <div class="scroll-progress" :style="{ width: `${scrollPercentage}%` }"/>
      </div>
    </PageScroll>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PageScroll from './components/PageScroll.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    PageScroll
  }
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
  height: 200vh;
}

.scroll-progress-container {
    bottom: 0;
    height: 6px;
    position: fixed;
    left: 0;
    width: 100%;
}

.scroll-progress {
    background-color: green;
    height: 100%;
}
</style>
