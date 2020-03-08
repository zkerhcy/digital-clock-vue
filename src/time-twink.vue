<template>
  <div class="time-twink">
    <svg class="dot" v-show="twink" version="1.1" xmlns="http://www.w3.org/2000/svg">
      <circle :fill="color" cx="50%" cy="30%" r="5%" />
      <circle :fill="color" cx="50%" cy="70%" r="5%" />
    </svg>
  </div>
</template>

<script>
export default {
  name: 'time-twink',
  data() {
    return {}
  },
  props: {
    color: {
      type: String
    },
    twink: {
      type: Boolean,
      default: true
    }
  }
}
</script>

<style lang='less' scoped>
.time-twink {
  width: 100%;
  .dot {
    width: 100%;
    height: 100%;
  }
}
</style>
