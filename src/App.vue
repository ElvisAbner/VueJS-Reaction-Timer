<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <button @click="isPlaying = false" :disabled="!isPlaying">End game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="showResult"> Reaction Time: {{ score }} ms</p>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results"

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResult: false,
      score: null
    }
  },
  methods: {
    start() {
      //set time amount (ms)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;

}

button:active {
  box-shadow: 2px 2px 5px green;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
  pointer-events: none;

}
</style>
