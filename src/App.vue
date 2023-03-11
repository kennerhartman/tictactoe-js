<template>
  <BoardGame/>
</template>

<script>
import BoardGame from './components/BoardGame.vue'

export default {
  name: 'App',
  components: {
    BoardGame
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

.X, .O {
  height: 0.1px;
  width: 0.1px;
  font-size: 5vmax;
  margin: 0;
}

.O {
  color: red;
}

.X {
  color: white;
}

#goFirst {
  font-style: italic;
  font-weight: 700;
  font-size: 24px;
}
</style>
