<template >
  <div class="digital-number">
    <!-- <svg height="8%" viewBox="0 0 100 8" v-show="showTop" width="100%">
      <path :fill="color" d="M 10 0 L 90 0 L 95 28 L 87 100 L 13 100 L 5 28" />
    </svg>-->
    <div :style="{background: color}" class="top" v-show="showTop"></div>
    <div :style="{background: color}" class="rt" v-show="showRt"></div>
    <div :style="{background: color}" class="middle" v-show="showMiddle"></div>
    <div :style="{background: color}" class="rb" v-show="showRb"></div>
    <div :style="{background: color}" class="bottom" v-show="showBottom"></div>
    <div :style="{background: color}" class="lt" v-show="showLt"></div>
    <div :style="{background: color}" class="lb" v-show="showLb"></div>
  </div>
</template>

<script>
export default {
  name: 'digital-number',
  props: {
    num: {
      type: [Number, String],
      default: 8,
      validator: function(val) {
        return parseInt(val) >= 0 && parseInt(val) <= 9
      }
    },
    color: {
      type: String,
      default: 'red'
    }
  },
  computed: {
    showTop() {
      return parseInt(this.num) !== 1 && parseInt(this.num) !== 4
    },
    showMiddle() {
      return [2, 3, 4, 5, 6, 8, 9].indexOf(parseInt(this.num)) > -1
    },
    showBottom() {
      return [2, 3, 5, 6, 8, 9, 0].indexOf(parseInt(this.num)) > -1
    },
    showLt() {
      return [4, 5, 6, 8, 9, 0].indexOf(parseInt(this.num)) > -1
    },
    showLb() {
      return [2, 6, 8, 0].indexOf(parseInt(this.num)) > -1
    },
    showRt() {
      return parseInt(this.num) !== 5 && parseInt(this.num) !== 6
    },
    showRb() {
      return parseInt(this.num) !== 2
    }
  }
}
</script>

<style lang='less' scoped>
.digital-number {
  float: left;
  position: relative;
  .top {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 8%;
    clip-path: polygon(10% 0, 90% 0, 95% 28%, 87% 100%, 13% 100%, 5% 28%);
  }
  .middle {
    position: absolute;
    width: 100%;
    height: 8%;
    top: 50%;
    transform: translateY(-50%);
    clip-path: polygon(
      12.5% 0,
      87.5% 0,
      94% 50%,
      87.5% 100%,
      12.5% 100%,
      6% 50%
    );
  }
  .bottom {
    position: absolute;
    width: 100%;
    bottom: 0;
    height: 8%;
    clip-path: polygon(13% 0, 87% 0, 95% 72%, 90% 100%, 10% 100%, 5% 72%);
  }
  .lt {
    position: absolute;
    width: 12%;
    height: 50%;
    top: 0;
    left: 0;
    clip-path: polygon(38% 5%, 100% 16%, 100% 91.5%, 45% 99.5%, 0 93.4%, 0 9%);
  }
  .lb {
    position: absolute;
    width: 12%;
    height: 50%;
    bottom: 0;
    left: 0;
    clip-path: polygon(45.2% 0.6%, 100% 8.5%, 100% 84%, 38% 95%, 0 91%, 0 7.5%);
  }
  .rt {
    position: absolute;
    width: 12%;
    height: 50%;
    top: 0;
    right: 0;
    clip-path: polygon(62% 5%, 100% 9%, 100% 93.4%, 55% 99.5%, 0 91.5%, 0 16%);
  }
  .rb {
    position: absolute;
    width: 12%;
    height: 50%;
    bottom: 0;
    right: 0;
    clip-path: polygon(54.8% 0.6%, 100% 7.5%, 100% 91%, 62% 95%, 0 84%, 0 8.5%);
  }
}
</style>
