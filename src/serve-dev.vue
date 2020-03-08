<template>
  <div id="app">
    <h1>Digital Clock Vue</h1>
    <!-- 4:1 -->
    <digital-clock-vue
      color="red"
      showSeconds
      style="background: black; width: 400px; height: 100px;"
    />
    <p>without seconds</p>
    <!-- 8:3 -->
    <digital-clock-vue color="#39af78" style="background: #2f4053; width: 240px; height: 90px;" />
    <h2>Digital Number</h2>
    <div>
      <digital-number
        :key="item"
        :num="item"
        color="#1973de"
        style="width: 45px; height:75px; margin-left: 2px;"
        v-for="item in Array.apply(null, {length: 10}).map((_, i) => i)"
      ></digital-number>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import DigitalClockVue from '@/digital-clock-vue'
import DigitalNumber from '@/digital-number'

export default {
  name: 'ServeDev',
  components: {
    DigitalClockVue,
    DigitalNumber
  }
}
</script>
