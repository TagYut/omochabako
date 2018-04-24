<template>
  <div class="tarot">
    <h1 class="tarot__title">tarot</h1>
    <div class="tarot__box">
      <div class="tarot__view">
        <canvas id="canvas" @click="canvasBall">ああああ</canvas>
      </div>
      <div class="tarot__input">
        <p>{{ randam }} をつかって乱数をつくるぞ</p>
        <input v-model="randam" placeholder="ここになんかかきこめ">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      randam: 'こいつ'
    }
  },
  methods: {
    canvasBall: function () {
      var canvas = document.getElementById('canvas')
      if (canvas.getContext) {
        var context = canvas.getContext('2d')
        context.fillRect(20, 40, 50, 100)
        context.strokeStyle = 'rgb(00,00,255)'
        context.fillStyle = 'rgb(255,00,00)'
        context.strokeRect(200, 80, 100, 50)
        context.arc(150, 75, 60, Math.PI * 1, Math.PI * 2, true)
        context.fill()
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped style lang="scss">
* {
  box-sizing: border-box;
}
canvas {
  height: 300px;
  width: 600px;
}
.tarot {
  &__title {
    border: 2px solid black;
    border-bottom-width: 0;
    margin: 0 auto;
    width: 604px;
  }
  &__box {
    border: 2px solid black;
    margin: 0 auto;
    height: 400px;
    width: 604px;
  }
  &__view {
    border-bottom: 2px solid black;
    margin: 0 auto;
    height: 300px;
    width: 600px;
  }
  &__input {
    height: 100px;
  }
}
</style>
