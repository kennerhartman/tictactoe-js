<template>
    <div>
        <div id="goFirst"></div>
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
    </div>
</template>

<script>
    let shape = 0   // determines what HTML content to generate; X's or O's 

    if(Math.round(Math.random()) === 1) {   // determines if X or O goes first
        shape = 1
    }
    
    // once the entire page and all content has been loaded, a new element will be created to tell if X or O is going first

    window.onload = function() { 
        if(shape === 1) {
            const goFirst = document.createElement('p')
            goFirst.textContent = "X is first!"
            document.getElementById('goFirst').appendChild(goFirst);
        } else {
            const goFirst = document.createElement('p')
            goFirst.textContent = "O is first!"
            document.getElementById('goFirst').appendChild(goFirst);
        }
    }

    export default {
        name: 'BoardGame',
        methods: {
            addShape(event) {
                const elementID = event.target.id   // targets the ID of the <div> clicked

                // variables for generating HTML content for X's and O's

                const pO = document.createElement('p')
                pO.textContent = "O"
                pO.className = "O"

                const pX = document.createElement('p')
                pX.textContent = "X"
                pX.className = "X"   
                
                // Logic for generating HTML content (X's or O's) content when any <div> is clicked

                if(!event.target.hasChildNodes()) {   // if the target element does not have a child element
                    if(shape === 0) {
                        document.body.appendChild(pO)
                        document.getElementById(elementID).appendChild(pO);
                        shape++
                    } else if(shape === 1) {
                        document.body.appendChild(pX)
                        document.getElementById(elementID).appendChild(pX);
                        shape--
                    }
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
