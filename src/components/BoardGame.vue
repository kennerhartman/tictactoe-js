<template>
  <div class="board">
    <div class="cell" id="one" @click="addShape($event)"></div>
    <div class="cell" id="two" @click="addShape($event)"></div>
    <div class="cell" id="three" @click="addShape($event)"></div>
    <div class="cell" id="four" @click="addShape($event)"></div>
    <div class="cell" id="five" @click="addShape($event)"></div>
    <div class="cell" id="six" @click="addShape($event)"></div>
    <div class="cell" id="seven" @click="addShape($event)"></div>
    <div class="cell" id="eight" @click="addShape($event)"></div>
    <div class="cell" id="nine" @click="addShape($event)"></div>
  </div>
</template>

<script>
// const shape = 0

    export default {
        name: 'BoardGame',
        methods: {
            addShape(event) {
                const elementID = event.target.id
                
                const pO = document.createElement('p')
                pO.textContent = "O"
                pO.className = "O"

                const pX = document.createElement('p')
                pX.textContent = "X"
                pX.className = "X"
                
                if(!event.target.hasChildNodes()) {   // if the target element does not have a child element
                    document.body.appendChild(pO)
                    document.getElementById(elementID).appendChild(pO);
                }
            }
        }
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
