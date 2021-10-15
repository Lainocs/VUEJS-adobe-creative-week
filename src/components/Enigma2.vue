<template>
    <div class="card">
        <div class="colors">
            <div>Bague</div>
            <div>Montre</div>
            <div>Bracelets</div>
            <div>Boucles d'oreille</div>
        </div>
        <div class="colors">
            <input type="button" @click="changeColor1()" id="color1" style="background-color: blue; width: 40px; height: 40px;">
            <input type="button" @click="changeColor2()" id="color2" style="background-color: yellow; width: 40px; height: 40px;">
            <input type="button" @click="changeColor3()" id="color3" style="background-color: green; width: 40px; height: 40px;">
            <input type="button" @click="changeColor4()" id="color4" style="background-color: red; width: 40px; height: 40px;">
        </div>
    </div>
</template>

<script>
    export default {
        name: "Enigma2",
        props: [
            'era'
        ],
        data() {
            return {
                sequence: ['', '', '', ''],
                combinaison: ['green', 'blue', 'red', 'yellow'],
                color1: '',
                color2: '',
                color3: '',
                color4: '',
            }
        },
        methods: {
            verify() {
                this.sequence = [this.color1, this.color2, this.color3, this.color4]
                if(this.sequence[0] == this.combinaison[0] && this.sequence[1] == this.combinaison[1] && this.sequence[2] == this.combinaison[2] && this.sequence[3] == this.combinaison[3]) {
                    this.$emit('enigma', '3')
                    this.$emit('view3', false)
                }
            },
            changeColor1() {
                let color1 = document.getElementById('color1')
                if(color1.style.backgroundColor == 'blue') {
                    color1.style.backgroundColor = 'yellow'
                    this.color1 = 'yellow'
                } else if(color1.style.backgroundColor == 'yellow') {
                    color1.style.backgroundColor = 'green'
                    this.color1 = 'green'
                } else if(color1.style.backgroundColor == 'green') {
                    color1.style.backgroundColor = 'red'
                    this.color1 = 'red'
                } else {
                    color1.style.backgroundColor = 'blue'
                    this.color1 = 'blue'
                }
                this.verify()
            },
            changeColor2() {
                let color2 = document.getElementById('color2')
                if(color2.style.backgroundColor == 'blue') {
                    color2.style.backgroundColor = 'yellow'
                    this.color2 = 'yellow'
                } else if(color2.style.backgroundColor == 'yellow') {
                    color2.style.backgroundColor = 'green'
                    this.color2 = 'green'
                } else if(color2.style.backgroundColor == 'green') {
                    color2.style.backgroundColor = 'red'
                    this.color2 = 'red'
                } else {
                    color2.style.backgroundColor = 'blue'
                    this.color2 = 'blue'
                }
                this.verify()
            },
            changeColor3() {
                let color3 = document.getElementById('color3')
                if(color3.style.backgroundColor == 'blue') {
                    color3.style.backgroundColor = 'yellow'
                    this.color3 = 'yellow'
                } else if(color3.style.backgroundColor == 'yellow') {
                    color3.style.backgroundColor = 'green'
                    this.color3 = 'green'
                } else if(color3.style.backgroundColor == 'green') {
                    color3.style.backgroundColor = 'red'
                    this.color3 = 'red'
                } else {
                    color3.style.backgroundColor = 'blue'
                    this.color3 = 'blue'
                }
                this.verify()
            },
            changeColor4() {
                let color4 = document.getElementById('color4')
                if(color4.style.backgroundColor == 'blue') {
                    color4.style.backgroundColor = 'yellow'
                    this.color4 = 'yellow'
                } else if(color4.style.backgroundColor == 'yellow') {
                    color4.style.backgroundColor = 'green'
                    this.color4 = 'green'
                } else if(color4.style.backgroundColor == 'green') {
                    color4.style.backgroundColor = 'red'
                    this.color4 = 'red'
                } else {
                    color4.style.backgroundColor = 'blue'
                    this.color4 = 'blue'
                }
                this.verify()
            },
        },
    }
</script>

<style>
    .card {
        padding: 50px;
        background-color: rgba(322, 322, 322, 0.5);
    }
    .colors {
        color: rgb(34, 34, 34);
        font-size: 20px;
        font-weight: bold;
        display: flex;
        width: 100%;
        justify-content: space-between;
    }
    #color1, #color2, #color3, #color4{
        border-radius: 50%;
        border: none;
        box-shadow: none;
        transition: 0.2s;
    }
    #color1:hover, #color2:hover, #color3:hover, #color4:hover{
        box-shadow: 3px 3px 3px rgb(105, 105, 105);
    }
</style>