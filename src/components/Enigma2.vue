<template>
    <div class="card">
        <div class="colors">
            <button @click="changeColor1()" id="color1" style="background-color: black; width: 40px; height: 40px;"></button>
            <button @click="changeColor2()" id="color2" style="background-color: yellow; width: 40px; height: 40px;"></button>
            <button @click="changeColor3()" id="color3" style="background-color: green; width: 40px; height: 40px;"></button>
            <button @click="changeColor4()" id="color4" style="background-color: red; width: 40px; height: 40px;"></button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Enigma2",
        props: [
            'era'
        ],
        methods: { 
            changeColor1() {
                let color1 = document.getElementById('color1')
                if(color1.style.backgroundColor == 'black') {
                    color1.style.backgroundColor = 'yellow'
                } else if(color1.style.backgroundColor == 'yellow') {
                    color1.style.backgroundColor = 'green'
                } else if(color1.style.backgroundColor == 'green') {
                    color1.style.backgroundColor = 'red'
                } else {
                    color1.style.backgroundColor = 'black'
                }
            },
            changeColor2() {
                let color2 = document.getElementById('color2')
                if(color2.style.backgroundColor == 'black') {
                    color2.style.backgroundColor = 'yellow'
                } else if(color2.style.backgroundColor == 'yellow') {
                    color2.style.backgroundColor = 'green'
                } else if(color2.style.backgroundColor == 'green') {
                    color2.style.backgroundColor = 'red'
                } else {
                    color2.style.backgroundColor = 'black'
                }
            },
            changeColor3() {
                let color3 = document.getElementById('color3')
                if(color3.style.backgroundColor == 'black') {
                    color3.style.backgroundColor = 'yellow'
                } else if(color3.style.backgroundColor == 'yellow') {
                    color3.style.backgroundColor = 'green'
                } else if(color3.style.backgroundColor == 'green') {
                    color3.style.backgroundColor = 'red'
                } else {
                    color3.style.backgroundColor = 'black'
                }
            },
            changeColor4() {
                let color4 = document.getElementById('color4')
                if(color4.style.backgroundColor == 'black') {
                    color4.style.backgroundColor = 'yellow'
                } else if(color4.style.backgroundColor == 'yellow') {
                    color4.style.backgroundColor = 'green'
                } else if(color4.style.backgroundColor == 'green') {
                    color4.style.backgroundColor = 'red'
                } else {
                    color4.style.backgroundColor = 'black'
                }
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
        display: flex;
        width: 100%;
        justify-content: space-around;
    }
</style>