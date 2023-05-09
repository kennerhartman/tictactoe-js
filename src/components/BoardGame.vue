<!--
//
// Copyright (c) Kenner Hartman. All rights reserved.
// Licensed under the MIT license. See LICENSE.md file in the project root for details.
//
-->

<template>
    <div>
        <div class="title">
            <span id="goFirstSpan" style="display: inline-block;"></span>
            <button style="display: ; margin-left: 25px;" @click="restartGame">Restart</button>
        </div>
        <table>
            <tr>
                <td id="one" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td class="vert" id="two" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td id="three" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
            </tr>
            <tr>
                <td class="hori" id="four" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td class="vert hori" id="five" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td class="hori" id="six" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
            </tr>
            <tr>
                <td id="seven" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td class="vert" id="eight" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
                <td id="nine" @mousedown="addShape($event)" @mouseup="checkIfWin"></td>
            </tr>
        </table>
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
            goFirst.id = "paragraph"
            document.getElementById('goFirstSpan').appendChild(goFirst)
        } else {
            const goFirst = document.createElement('p')
            goFirst.textContent = "O is first!"
            goFirst.id = "paragraph"
            document.getElementById('goFirstSpan').appendChild(goFirst)
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
                        document.getElementById(elementID).appendChild(pO)
                        shape++
                        this.numbers[elementID] = "O"
                    } else if(shape === 1) {
                        document.body.appendChild(pX)
                        document.getElementById(elementID).appendChild(pX)
                        shape--
                        this.numbers[elementID] = "X"
                    }
                }
            },
            checkIfWin() {
                // variables for accessing DOM

                const goFirst = document.querySelector('#goFirstSpan')
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
            },
            restartGame() {
                shape = 0 // because in the method, 'checkIfWin,' we set shape to -1, the game cannot start unless it is set to 0 or 1 

                // clears the winning text set in the method 'checkIfWin'
                
                document.getElementById('goFirstSpan').innerHTML = ""

                // first thing we need to do to reset the game by clearing the 'numbers' object; achieved by an array and for loop

                const arrayOfID = ["one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]

                for(var i = 0; i < arrayOfID.length; i++) {
                    // looping through the 'numbres' object and finding values to set to an empty string by the 'arrayOfId' array
                    this.numbers[arrayOfID[i]] = ""    
                }

                // next, we need to clear all <p> elements from the DOM with a class of 'O' and 'X'
                
                const elementO = document.getElementsByClassName('O')   // controls all O's
                const elementX = document.getElementsByClassName('X')   // controls all X's

                while(elementO.length > 0){
                    elementO[0].parentNode.removeChild(elementO[0])    // removes all O's
                }

                while(elementX.length > 0){
                    elementX[0].parentNode.removeChild(elementX[0])    // removes all X's
                }
            
                if(Math.round(Math.random()) === 1) {   // redetermines if X or O goes first
                    shape = 1
                }

                // creates a new element to append to the DOM to tell who is going first

                const goFirst = document.createElement('p')
                goFirst.id = "paragraph"
                document.getElementById('goFirstSpan').appendChild(goFirst)

                if(shape === 1) {
                    document.getElementById('paragraph').innerHTML = "X is first!"
                } else {
                    document.getElementById('paragraph').innerHTML = "O is first!"
                }
            },
        },
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
td {
  width: 100px;
  height: 100px;
}

td:hover {
  background: rgb(224, 224, 224);  
  cursor: pointer;
}

table {
  margin: 15px auto;
}
.vert {
  border-left: 2px solid black;
  border-right: 2px solid black;
}
.hori {
  border-top: 2px solid black;
  border-bottom: 2px solid black;
}
</style>