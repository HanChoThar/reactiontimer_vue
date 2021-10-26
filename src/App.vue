<template>
  <h1 class="heading">ninja reaction timer</h1>
  <button @click="start" :disabled="track" class="btn">Start</button>
  <Block v-if="track" :delay="delay" @end="endgame"/>
  <Result v-if="showScore" :pass="score"/>
</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Block , Result},
  data() {
    return {
      track: false,
      delay: null,
      score: null,
      showScore: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000,
      this.track = true
      this.showScore = false
    },
    endgame(reactionTime) {
      this.score = reactionTime
      this.track = false
      this.showScore = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.heading{
  font-size: 3rem;
  color: rgb(21, 131, 49);
}

.btn{
  padding: 0.5rem;
  border-radius: 5px;
  background: green;
  color: white;
  border: 1px solid transparent;
  cursor: pointer;
}
</style>
