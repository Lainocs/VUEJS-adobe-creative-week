<template>
    <div class="card">
        <h2>Le jeu du pendu</h2>
        <div class="letter">
            <div v-for="letter in displayLetters" :key="letter">
            {{letter}}
            </div>
        </div>
        <div class="test">
            <!-- the @click listener will call the tryLetter method after the click event
        on one of the letters -->
            <div class="letter allletters">
                <div @click="tryLetter(letter)" v-for="letter in possibleLetters" class="possibleLetter" :key="letter">
                {{letter}}
                </div>
            </div>
            
            <div id="conditionalrendering">
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="350px" height="275px" viewBox="0 0 350 300" preserveAspectRatio="xMidYMid meet">
                    <line v-if="strikes > 0" x1="80" y1="257" x2="260" y2="257" style="stroke:black;" />
                    <line v-if="strikes > 1" x1="100" y1="257" x2="100" y2="40" style="stroke:black;" />
                    <line v-if="strikes > 2" x1="100" y1="40" x2="230" y2="40" style="stroke:black;" />
                    <line v-if="strikes > 3" x1="100" y1="80" x2="130" y2="40" style="stroke:black;" />
                    <line v-if="strikes > 4" x1="230" y1="40" x2="230" y2="80" style="stroke:black;" />
                    <circle v-if="strikes > 5" cx="230" cy="90" style="fill:khaki;stroke:black;" r="20" />
                    <line v-if="strikes > 6" x1="230" y1="110" x2="230" y2="170" style="stroke:black;" />
                    <line v-if="strikes > 7" x1="230" y1="140" x2="250" y2="120" style="stroke:black;" />
                    <line v-if="strikes > 8" x1="230" y1="140" x2="210" y2="120" style="stroke:black;" />
                    <line v-if="strikes > 9" x1="230" y1="170" x2="250" y2="200" style="stroke:black;" />
                    <line v-if="strikes > 10" x1="230" y1="170" x2="210" y2="200" style="stroke:black;" />
                </svg>
            </div>
        </div>
        <div class="historique_letterinput">
        {{console}}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Hangman',
        props: [
            'era'
        ],
        data() {
            return {
                result : '',
                error: false,
                strikes: 0,
                displayLetters: ['','','','','','','','',''],
                wordLetters: ['S','Q','U','E','L','E','T','T','E'],
                possibleLetters: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'],
                console: 'Trouvez le mot qui vous servira d\'indice'
            }
        },
        methods: {
            tryLetter(letter) {
            for (let i = 0; i < this.displayLetters.length; i++) {
                if (letter === this.wordLetters[i]) {
                this.displayLetters.splice(i, 1, letter)
                }
            }
            if (letter != 'S' && letter != 'Q' && letter != 'U' && letter != 'E' && letter != 'L' && letter != 'T') {
                this.strikes = this.strikes + 1
            }
            
            let displayletters = this.displayLetters.toString()
            let allletters = displayletters.replace(/,/g, '')
            if(allletters == 'SQUELETTE') {
                this.$emit('enigma', '1')
                this.$emit('view1', false)
            }
            this.console = 'La lettre ' + letter
            },

            verifyLetter() {
                if(this.displayLetters.length == 9) {
                    console.log('aled')
                }
            }
        }
    }
</script>

<style>
    .card {
        padding: 20px;
        background-color: rgba(322, 322, 322, 0.8);
    }

    .allletters {
        width: 40vw;
    }

    #conditionalrendering {
        width: 40vw;
    }

    .test {
        display: flex;
        flex-wrap: wrap;
    }

    .letter {
        flex-wrap: wrap;
        display: flex;
        justify-content: center;
        padding: 30px;
        color: black;
        font-size: 22px;
        font-weight: bold;
    }
    .possibleLetter {
        font-weight: bold;
        padding: 10px;
        margin: 10px;
        color: rgb(61, 37, 0);
        font-size: 20px;
        border: 2px solid black;
    }
    .historique_letterinput {
        color: rgb(61, 37, 0);
        font-weight: bold;
        font-size: 22px;
    }
</style>