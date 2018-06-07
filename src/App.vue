<template>
  <div id="app">
    <VueportPageScroll>
      <div
        class="scroll-progress-rotate"
        slot-scope="{ scrollY, scrollPcnt }"
        :style="{ transform: `translateX(${scrollPcnt}%) rotate(${scrollY}deg)` }"
      >
        AAAAA
      </div>
    </VueportPageScroll>

    <VueportElementPosition>
      <div class="mt-full" slot-scope="{ boundingClientRect, centerPcnt }">
        <span v-if="boundingClientRect">
          {{ boundingClientRect.top }}
        </span>
        <span v-if="boundingClientRect" class="bottom">
          {{ centerPcnt }}
        </span>
      </div>
    </VueportElementPosition>

    <VueportPageScroll>
      <div class="scroll-progress-container" slot-scope="{ scrollPcnt }">
          <div class="scroll-progress" :style="{ width: `${scrollPcnt}%` }"/>
      </div>
    </VueportPageScroll>
  </div>
</template>

<script>
import VueportPageScroll from './components/VueportPageScroll.vue'
import VueportElementPosition from './components/VueportElementPosition.vue'

export default {
  name: 'app',
  components: {
    VueportPageScroll,
    VueportElementPosition
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

.scroll-progress-rotate {
  position: fixed;
  top: 20px;
  left: 20px;
  transform-origin: center;
}

.bottom {
  position: fixed;
  bottom: 0;
  left: 0;
}

.mt-full {
  margin-top: 100vh;
}
</style>
