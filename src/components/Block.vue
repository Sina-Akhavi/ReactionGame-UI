<template>
  <div v-if="isShownClickBtn" @click="stopTimer" class="click-btn">click</div>
</template>

<script>

  export default {
    props: ['delay', 'end'],
    data() {
      return {
        isShownClickBtn: false,
        timer: null,
        reactionTime: 0
      }
    },
    
    methods: {
      stopTimer() {
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
      },

      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 5
        }, 5)
      }
    },

    mounted() {
      setTimeout(() => {
        this.isShownClickBtn = !this.isShownClickBtn
        this.startTimer()
      }, this.delay)
    },

  }

</script>

<style>

.click-btn {
  background-color: cyan;
  width: 20%;
  padding: 100px 0;
  margin: 40px auto;
  border-radius: 15px;
  font-weight: bold;
  font-family: 'Times New Roman', Times, serif;
  font-size: xx-large;
  cursor: pointer;
}

</style>