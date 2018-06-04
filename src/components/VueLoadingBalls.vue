<template>
  <svg :width="width" :height="height">
    <filter id="dropshadow" x="-20%" y="-20%" width="140%" height="140%">
      <feOffset result="offOut" in="SourceAlpha" dx="0" dy="2" />
      <feGaussianBlur result="blurOut" in="offOut" stdDeviation="1" />
      <feComponentTransfer>
        <feFuncA result="opacityOut" in="blurOut" type="linear" slope="0.23"/>
      </feComponentTransfer>
      <feBlend in="SourceGraphic" in2="opacityOut" mode="normal" />
    </filter>
    <circle v-for="(ball, index) in balls"
            :key="index"
            :cx="ball.cx"
            :cy="ball.cy"
            :r="ball.r"
            :fill="ball.fill"
            style="filter:url(#dropshadow)" />
  </svg>
</template>

<script>
export default {
  name: 'VueLoadingBalls',
  props: {
    width: { type: [Number, String], default: 300 },
    height: { type: [Number, String], default: 150 },
    color: { type: String, default: '#333333' },
    count: { type: [Number, String], default: 3 },
    radius: { type: [Number, String], default: 10 }
  },
  data: () => ({
    currentAnimationTime: 0,
    balls: []
  }),
  computed: {
    $_width () {
      return parseInt(this.width)
    },
    $_height () {
      return parseInt(this.height)
    },
    $_count () {
      return parseInt(this.count)
    },
    $_radius () {
      return parseInt(this.radius)
    },
    centerY () {
      return Math.floor(this.$_height / 2)
    },
    centerX () {
      return Math.floor(this.$_width / 2)
    },
    amplitude () {
      return Math.min(Math.floor(this.$_height / 4), this.$_radius * 4)
    }
  },
  methods: {
    initBalls () {
      const offsetX = this.$_radius * 3
      const offsetMultiple = Math.floor(this.$_count / 2)
      const offsetEven = !(this.$_count % 2) ? Math.floor(offsetX / 2) : 0
      for (let i = 0; i < this.$_count; i++) {
        this.balls.push({
          cx: this.centerX - offsetX * (i - offsetMultiple) - offsetEven,
          cy: this.centerY,
          r: this.$_radius,
          fill: this.color
        })
      }
    },
    animate () {
      this.balls.forEach((ball, index) => {
        ball.cy = this.sinY(-index)
      })
      this.currentAnimationTime += 0.15
      requestAnimationFrame(this.animate)
    },
    sinY (shift = 0) {
      return (
        this.centerY +
        this.amplitude * Math.sin(this.currentAnimationTime - shift)
      )
    }
  },
  created () {
    this.initBalls()
  },
  mounted () {
    this.animate()
  }
}
</script>
