<template>
  <div class="board">
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
  </div>
</template>

<script>
export default {
  name: 'BoardGame',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.board {
  padding-top: 5px;
  aspect-ratio: 1 / 1;
  width: 45%;
  height: 45%;
  
  display: flex;                       /* establish flex container */
  flex-wrap: wrap;                     /* enable flex items to wrap */
  justify-content: space-around;
  border: 3px solid;
  margin-left: auto;
  margin-right: auto;
}
.cell {
  flex: 0 0 32%;                       /* don't grow, don't shrink, width */
  margin-bottom: 5px;
  background-color: #999;
}

.cell:hover {
  opacity: 0.5;
}
</style>
