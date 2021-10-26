<template>
  <div style="font-weight: bold;">
    <p>reaction time score is {{ pass }} ms</p>
    <p>{{ fastRate }}</p>
  </div>
</template>

<script>
  export default {
    props : ['pass'],
    data() {
      return {
        fastRate : null
      }
    },
    mounted() {
      if(this.pass < 250){
        this.fastRate = 'You are fast like ninja'
      } else if(this.pass < 450 ){
        this.fastRate = 'You are not bad'
      } else {
        this.fastRate = 'You need to try more become ninja'
      }
    }
  }
</script>