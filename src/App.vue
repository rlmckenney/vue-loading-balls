<template>
  <div id="app">
    <!-- <BuildDemo message="Hello Vue" /> -->
    <h1>Vue Loading Balls Demos</h1>
    <h2>Simple defaults</h2>
    <code><pre>&lt;loading-balls /&gt;</pre></code>
    <bouncing-balls v-if="isLoading" />
    <section v-else>Content here ...</section>

    <h2>Customize options</h2>
    <code><pre>&lt;loading-balls count="4" color="#4b0082" /&gt;</pre></code>
    <bouncing-balls v-if="isLoading" count="4" color="#4b0082" />
    <section v-else>Content here ...</section>
  </div>
</template>

<script>
import VueLoadingBalls from '@/components/VueLoadingBalls'

export default {
  name: 'app',
  components: {
    BouncingBalls: VueLoadingBalls
  },
  data: () => ({
    isLoading: true
  })
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
