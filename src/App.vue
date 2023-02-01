<template>
  <h1>Reaction Time Game</h1>
  <button class="play-btn" @click="startGame" :disabled="isDisable">play</button>
  <Block v-if="isMount" :delay="delay" @end="endGame"/>
  <Result v-if="isShownResult" :reactionTime="score" />
</template>


<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {

  components: { Block, Result },

  data() {
    return {
      isDisable: false,
      isMount: false,
      isShownResult: false,
      delay: null,
      timer: null,
      reactionTime: 0,
      score: null
    }
  },

  methods: {
    startGame() {
      this.isShownResult = false
      this.isDisable = true  
      this.delay = 2000 + Math.random() * 3000
      this.isMount = !this.isMount
    },

    endGame(reactionTime) {
      this.score = reactionTime
      this.isDisable = false
      this.isShownResult = true
      this.isMount = false
    }
  }

}

</script>

<style>

h1 {
  font-family: cursive
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.play-btn {
  background: cyan;
  border-radius: 5px;
  padding: 10px 15px;
  border: 1px solid black;
  cursor: pointer;
}

</style>
