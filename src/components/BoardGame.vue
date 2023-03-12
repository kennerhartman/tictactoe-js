<template>
    <div>
        <span id="goFirst"></span>
        <div class="board">
            <div class="cell" id="one" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="two" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="three" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="four" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="five" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="six" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="seven" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="eight" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
            <div class="cell" id="nine" @mousedown="addShape($event)" @mouseup="checkIfWin"></div>
        </div>
    </div>
</template>

<script>
    let shape = 0   // determines what HTML content to generate; X's or O's; if shape = -1, game is over.

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
        data() {
            return {
                // the 'numbers' object is constantly being changed.  each item in the object is empty.  
                // each item has a similar name just as the <div> IDs, but they are not linked.
                // once a <div> gets clicked on, the addShape() method will take its ID, access this object, then store either X or O in the 
                // right item as a string.  this object is displayed as if it were a tic-tac-toe board.
                numbers: {  
                    one: "", two: "", three: "",
                    four: "", five: "", six: "",
                    seven: "", eight: "", nine: ""
                }
            }
        },
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
                
                // logic for generating HTML content (X's or O's) content when any <div> is clicked

                if(!event.target.hasChildNodes()) {   // if the target element does not have a child element
                    if(shape === 0) {
                        document.body.appendChild(pO)
                        document.getElementById(elementID).appendChild(pO);
                        shape++
                        this.numbers[elementID] = "O"
                    } else if(shape === 1) {
                        document.body.appendChild(pX)
                        document.getElementById(elementID).appendChild(pX);
                        shape--
                        this.numbers[elementID] = "X"
                    }
                }
            },
            checkIfWin() {
                // variables for accessing DOM

                const goFirst = document.querySelector('#goFirst')
                goFirst.textContent = ""

                // logic for checking if a win occured according to traditional tic-tac-toe rules
                // called everytime on a mouse up event within the <div> squares

                // diagonal win check

                if(this.numbers['one'] == "X" && this.numbers['five'] == "X" && this.numbers['nine'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['one'] == "O" && this.numbers['five'] == "O" && this.numbers['nine'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                if(this.numbers['three'] == "X" && this.numbers['five'] == "X" && this.numbers['seven'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['three'] == "O" && this.numbers['five'] == "O" && this.numbers['seven'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // row one win check

                if(this.numbers['one'] == "X" && this.numbers['two'] == "X" && this.numbers['three'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['one'] == "O" && this.numbers['two'] == "O" && this.numbers['three'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // row two win check

                if(this.numbers['four'] == "X" && this.numbers['five'] == "X" && this.numbers['six'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['four'] == "O" && this.numbers['five'] == "O" && this.numbers['six'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // row three win check

                if(this.numbers['seven'] == "X" && this.numbers['eight'] == "X" && this.numbers['nine'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['seven'] == "O" && this.numbers['eight'] == "O" && this.numbers['nine'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // column one win check

                if(this.numbers['one'] == "X" && this.numbers['four'] == "X" && this.numbers['seven'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['one'] == "O" && this.numbers['four'] == "O" && this.numbers['seven'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // column two win check

                if(this.numbers['two'] == "X" && this.numbers['five'] == "X" && this.numbers['eight'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['two'] == "O" && this.numbers['five'] == "O" && this.numbers['eight'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }

                // column three win check

                if(this.numbers['three'] == "X" && this.numbers['six'] == "X" && this.numbers['nine'] == "X" ) {
                    shape = -1
                    goFirst.textContent = "X won!"
                } else if(this.numbers['three'] == "O" && this.numbers['six'] == "O" && this.numbers['nine'] == "O" ) {
                    shape = -1
                    goFirst.textContent = "O won!"
                }
            }
        },
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
