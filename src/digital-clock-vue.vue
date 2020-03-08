<template>
  <div class="digital-clock-vue">
    <digital-number :color="color" :num="h1" :style="{width: numWidth, height: '100%'}"></digital-number>
    <digital-number :color="color" :num="h2" :style="{width: numWidth, height: '100%'}"></digital-number>
    <time-twink :color="color" :style="{width: twinkWidth}" :twink="twink" class="twink"></time-twink>
    <digital-number :color="color" :num="m1" :style="{width: numWidth, height: '100%'}"></digital-number>
    <digital-number :color="color" :num="m2" :style="{width: numWidth, height: '100%'}"></digital-number>
    <time-twink
      :color="color"
      :style="{width: twinkWidth}"
      :twink="twink"
      class="twink"
      v-if="showSeconds"
    ></time-twink>
    <digital-number
      :color="color"
      :num="s1"
      :style="{width: numWidth, height: '100%'}"
      v-if="showSeconds"
    ></digital-number>
    <digital-number
      :color="color"
      :num="s2"
      :style="{width: numWidth, height: '100%'}"
      v-if="showSeconds"
    ></digital-number>
  </div>
</template>

<script>
import digitalNumber from './digital-number.vue'
import timeTwink from './time-twink.vue'
let requestAnimationFrame =
  window.requestAnimationFrame ||
  window.webkitRequestAnimationFrame ||
  window.mozRequestAnimationFrame ||
  window.oRequestAnimationFrame ||
  window.msRequestAnimationFrame ||
  function(callback) {
    setTimeout(callback, 1000 / 60)
  }
export default {
  components: { digitalNumber, timeTwink },
  data() {
    return {
      time: new Date()
    }
  },
  mounted() {
    requestAnimationFrame(this.addTime)
  },
  computed: {
    hours() {
      return this.time.getHours()
    },
    minutes() {
      return this.time.getMinutes()
    },
    seconds() {
      return this.time.getSeconds()
    },
    h1() {
      return this.hours < 10 ? 0 : parseInt((this.hours % 100) / 10)
    },
    h2() {
      return this.hours < 10 ? this.hours : parseInt(this.hours % 10)
    },
    m1() {
      return this.minutes < 10 ? 0 : parseInt((this.minutes % 100) / 10)
    },
    m2() {
      return this.minutes < 10 ? this.minutes : parseInt(this.minutes % 10)
    },
    s1() {
      return this.seconds < 10 ? 0 : parseInt((this.seconds % 100) / 10)
    },
    s2() {
      return this.seconds < 10 ? this.seconds : parseInt(this.seconds % 10)
    },
    twink() {
      return this.s2 % 2 === 0
    },
    numWidth() {
      return this.showSeconds ? '14%' : '22%'
    },
    twinkWidth() {
      return this.showSeconds ? '3%' : '6%'
    }
  },
  props: {
    color: {
      type: String,
      default: 'red'
    },
    showSeconds: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    addTime() {
      this.time = new Date()
      requestAnimationFrame(this.addTime)
    }
  }
}
</script>

<style lang='less' scoped>
.digital-clock-vue {
  box-sizing: border-box;
  .twink {
    height: 100%;
    float: left;
  }
  // padding: 1%;
  .digital-number {
    margin: 0 1%;
    &:first-child {
      margin-left: 0;
    }
    &:last-child {
      margin-right: 0;
    }
  }
}
</style>
