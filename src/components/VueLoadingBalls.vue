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
  name: 'loading-balls',
  props: {
    width: { type: Number, default: 300 },
    height: { type: Number, default: 150 },
    color: { type: String, default: '#333333' },
    count: { type: Number, default: 3 },
    radius: { type: Number, default: 10 }
  },
  data: () => ({
    currentAnimationTime: 0,
    balls: []
  }),
  computed: {
    centerY () {
      return Math.floor(this.height / 2)
    },
    centerX () {
      return Math.floor(this.width / 2)
    },
    amplitude () {
      return Math.min(Math.floor(this.height / 4), this.radius * 4)
    }
  },
  methods: {
    initBalls () {
      const offsetX = this.radius * 3
      const offsetMultiple = Math.floor(this.count / 2)
      const offsetEven = !(this.count % 2) ? Math.floor(offsetX / 2) : 0
      for (let i = 0; i < this.count; i++) {
        this.balls.push({
          cx: this.centerX - offsetX * (i - offsetMultiple) - offsetEven,
          cy: this.centerY,
          r: this.radius,
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
