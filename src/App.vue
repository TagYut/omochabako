<template>
  <div id="app">
    <img id="app__logo" :style="{animationDuration: spinLate + 'ms'}" @click="spinUp" src="./assets/logo.png">
    <h2 @click="spinStop">{{ fuckSpin }}</h2>
    <router-view/>
    <tarot></tarot>
  </div>
</template>

<script>
import tarot from './components/Tarot'

export default {
  data () {
    return {
      spinLate: 0,
      fuckSpin: '',
      areYouFuck: false,
      areYouSpin: false,
      areYouSpinUp: false,
      areYouSpinDown: false
    }
  },
  components: {
    tarot
  },
  methods: {
    spinUp: function () {
      if (this.areYouSpin) {
        if (this.areYouSpinUp) {
          this.spinLate = 100
          this.areYouSpinUp = false
          this.fuckSpin = 'No No No plz Click Me!'
        } else {
          this.spinLate = 1
          this.areYouSpinUp = true
          this.areYouFuck = true
          this.fuckSpin = 'Fuckyou Stop plz!'
        }
      } else {
        this.spinLate = 1000
        this.areYouSpin = true
      }
    },
    spinStop: function () {
      if (this.areYouFuck) {
        this.spinLate = 0
        this.areYouSpin = true
        this.areYouSpinDown = true
        this.fuckSpin = '...ok.Spinup plz'
        this.areYouFuck = false
      } else {
        this.spinLate = 2000
        this.fuckSpin = 'So Good too Slow'
      }
    }
  }
}
</script>

<style style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  &__logo {
    animation: spining linear infinite;
  }
  @keyframes spining {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}
</style>
