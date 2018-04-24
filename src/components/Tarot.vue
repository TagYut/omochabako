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
      var gl = canvas.getContext('webgl')
      if (canvas.getContext) {
        gl.viewport(0, 0, canvas.width, canvas.height)
        gl.clearColor(0, 0, 0, 1)
        gl.clear(gl.COLOR_BUFFER_BIT)
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
    height: 404px;
    width: 604px;
  }
  &__view {
    border-bottom: 2px solid black;
    margin: 0 auto;
    height: 302px;
    width: 600px;
  }
  &__input {
    height: 100px;
  }
}
</style>
