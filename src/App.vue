<template>
  <h1>Sammie Reaction Timer &#128526;</h1>
  <button @click= "start" :disabled= "isPlaying">Play</button>
  <Block v-if= "isPlaying" :delay= "delay" @end= "endGame"/>
  <Result v-if="showResult" :score="score"/>
 
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: 'App',
  components: { Block, Result},
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
  endGame(reactionTimer){
    this.score = reactionTimer
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
  color: blue;
  margin-top: 60px;
}
button{
  background: black;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.3;
  cursor: not-allowed;
}
</style>
