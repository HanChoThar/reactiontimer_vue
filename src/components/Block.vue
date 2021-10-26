<template>
  <div class="block" v-if="showBlock" @click="endTime">
    click me
  </div>
</template>

<script>
  export default {
    props : ['delay'],
    data() {
      return {
        showBlock: false,
        bridge: null,
        interactionTime: 0
      }
    },
    mounted() {
      setTimeout(() => {
        this.showBlock = true
        this.startTime()
        console.log(this.delay)
      }, this.delay)
    },
    methods: {
      startTime() {
        this.bridge = setInterval(() => {
          this.interactionTime += 10
        }, 10)
      },
      endTime() {
        clearInterval(this.bridge)
        this.$emit('end', this.interactionTime)
      }
    }

  }
</script>

<style>
  .block{
    width: 400px;
    background-color: green;
    border-radius: 25px;
    height: 200px;
    margin: 40px auto;
    text-align: center;
    padding: 100px 0;
    color: white;
    cursor: pointer;
  }
</style>