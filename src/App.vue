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
  font-size: 50px;
  margin: 0;
  
}

.O {
  color: red;
}

.X {
  color: black;
}

#goFirst {
  font-style: italic;
  font-weight: 700;
  font-size: 28px;
}
</style>
