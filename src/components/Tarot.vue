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
import * as THREE from 'three'

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
      // サイズを指定
      const width = 600
      const height = 300

      // レンダラーを作成
      const renderer = new THREE.WebGLRenderer({
        canvas: document.querySelector('canvas')
      })
      renderer.setPixelRatio(window.devicePixelRatio)
      renderer.setSize(width, height)

      // シーンを作成
      const scene = new THREE.Scene()

      // カメラを作成
      const camera = new THREE.PerspectiveCamera(45, width / height)
      camera.position.set(0, 0, +1000)

      // 箱を作成
      const geometry = new THREE.BoxGeometry(400, 400, 400)
      const material = new THREE.MeshNormalMaterial()
      const box = new THREE.Mesh(geometry, material)
      scene.add(box)

      tick()

      // 毎フレーム時に実行されるループイベントです
      function tick () {
        box.rotation.y += 0.01
        renderer.render(scene, camera) // レンダリング

        requestAnimationFrame(tick)
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
