<template>

  <div class="screen">
    <div id="content">
      <div @click="clicked1" class="border-enigma-1" v-if="enigma == 0 && era == 'Victorienne' && border1 == true"></div>
      <Hangman @enigma="getEnigma" v-if="enigma == 0 && view1 == true && era == 'Victorienne' && border1 == false" :era="era"/>

      <div @click="clicked2" class="border-enigma-2" v-if="enigma == 1 && era == 'Victorienne' && border2 == true"></div>
      <Enigma1 @enigma="getEnigma" v-if="enigma == 1 && view2 == true" :era="era" />

      <div @click="clicked3" class="border-enigma-3" v-if="enigma == 2 && era == 'Années 60' && border3 == true"></div>
      <Enigma2 @enigma="getEnigma" v-if="enigma == 2 && view3 == true" :era="era" />
    </div>
    <div class="era">
      {{era}}
      <button @click="changeEra">CHANGER D'EPOQUE</button>
    </div>
  </div>
  
</template>

<script>
import Enigma1 from './components/Enigma1.vue'
import Enigma2 from './components/Enigma2.vue'
import Hangman from './components/Hangman.vue'

export default {
  name: 'App',

  components: {
    Hangman,
    Enigma1,
    Enigma2,
  },
  data() {
    return {
      era: 'Victorienne',
      enigma: 0,

      border1: true,
      view1: false,

      border2: true,
      view2: false,

      border3: true,
      view3: false
    }
  },
  methods: {
    changeEra() {
      if(this.era == 'Victorienne') {
        this.era = 'Années 60'
      } else if(this.era == 'Années 60') {
        this.era = 'Victorienne'
      }
    },
    getEnigma(value) {
      this.enigma = value
    },

    clicked1() {
      this.border1 = false
      this.view1 = true
    },

    clicked2() {
      this.border2 = false
      this.view2 = true
    },

    clicked3() {
      this.border3 = false
      this.view3 = true
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  background-image: url('assets/musee.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.screen {
  height: 90vh;
  width: 90vw;
  flex-direction: column;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

#content {
  min-height: 80vh;
}

.border-enigma-1 {
  position: absolute;
  left: 40vw;
  top: 10vh;
  border: 2px solid black;
  margin: 100px 0;
  width: 10vw;
  height: 20vh;
}

.border-enigma-2 {
  position: absolute;
  left: 60vw;
  bottom: 10vh;
  border: 2px solid black;
  margin: 100px 0;
  width: 10vw;
  height: 10vh;
}

.border-enigma-3 {
  position: absolute;
  left: 60vw;
  bottom: 10vh;
  border: 2px solid black;
  margin: 100px 0;
  width: 5vw;
  height: 60vh;
}

.era {
  height: 10vh;
}
</style>
