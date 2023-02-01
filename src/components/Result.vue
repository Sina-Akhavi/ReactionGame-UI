<template>
  <p>you reacted in {{reactionTime}} ms</p>
  <h3>Your rank is {{setRank}}</h3>
</template>



<script>
export default {
  props: ['reactionTime'],

  computed: {
    setRank() {
      if (this.reactionTime <= 100) {
        return 'like wind !!!'
      } else if (this.reactionTime <= 300) {
        return 'good reaction !!!'
      } else if (this.reactionTime <= 400) {
        return 'not bad !!!'
      } else {
        return 'snail pace...'
      }
    }
  }

}
</script>


<style>
</style>