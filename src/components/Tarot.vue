<template>
  <div class="tarot">
    <h1 class="tarot__title">tarot</h1>
    <div class="tarot__box">
      <div class="tarot__view" ref="renderer"></div>
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
    // シーン
    const scene = new THREE.Scene()
    // レンダラ
    const renderer = new THREE.WebGLRenderer()
    renderer.setClearColor(0xFFFFFFF, 1.0)
    renderer.setSize(600, 300)
    // カメラ
    const camera = new THREE.PerspectiveCamera(30, 600 / 300, 0.1, 1000)
    camera.position.z = 5
    // ライト
    const light = new THREE.DirectionalLight(0xffffff)
    light.position.set(0, 0, 10)
    // モデル
    const geometry = new THREE.BoxGeometry(1, 1, 1)
    const material = new THREE.MeshStandardMaterial({ color: 0x00fff0 })
    const cube = new THREE.Mesh(geometry, material)
    return {
      msg: 'Welcome to Your Vue.js App',
      randam: 'こいつ',
      scene: scene,
      renderer: renderer,
      camera: camera,
      light: light,
      cube: cube
    }
  },

  created () {
    // === sceneにmodel,light, cameraを追加 ===
    this.scene.add(this.camera)
    this.scene.add(this.light)
    this.scene.add(this.cube)
  },

  mounted () {
    // === DOMを追加, animate ===
    this.$refs.renderer.appendChild(this.renderer.domElement)
    this.animate()
  },

  methods: {
    animate () {
      requestAnimationFrame(this.animate)
      this.cube.rotation.x += 0.005
      this.cube.rotation.y += 0.005
      this.renderer.render(this.scene, this.camera)
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
