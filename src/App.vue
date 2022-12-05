<template>
  <h1>How fast can u catch me?</h1>
  <button @click="start" :disabled="isPlaying" id="play">play</button>
  <div v-if="isPlaying">
    <BlockB :delay="delay" @endGame="endGame"/>
  </div>
  <div v-if="showResult">
    <ResultS :score="score"/>
  </div>
  
</template>

<script>
import BlockB from "./components/BlockB.vue"
import ResultS from "./components/ResultS.vue"

export default {
  name: 'App',
  components: {
    BlockB,
    ResultS
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResult: false
    }
  },
  methods: {
    start() {
      this.isPlaying= true;
      this.delay= 2000+Math.random()*5000;
      this.showResult= false;
    },
    endGame(score) {
      this.score= score;
      this.isPlaying= false;
      this.showResult= true;
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
#play {
  width: 100px;
  background-color: green;
  color: white;
  font-size: 22px;
  padding: 3px;
  border-radius: 3px;
}
</style>
