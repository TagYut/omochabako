<template>
  <div class="Tarot">
    <h1 class="Tarot__title">tarot</h1>
    <div class="Tarot__box">
      <div class="Tarot__view"></div>
      <div class="Tarot__input">
        <p>Please Input Your Birthday</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped style lang="scss">
* {
  box-sizing: border-box;
}
.Tarot {
  &__title {
    border: 2px solid black;
    border-bottom-width: 0;
    margin: 0 auto;
    width: 600px;
  }
  &__box {
    border: 2px solid black;
    margin: 0 auto;
    height: 400px;
    width: 600px;
  }
  &__view {
    border-bottom: 2px solid black;
    margin: 0 auto;
    height: 300px;
    width: 598px;
  }
  &__input {
    height: 100px;
  }
}
</style>
