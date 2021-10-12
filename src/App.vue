<template>

  <div class="screen">
    <div id="content">
      <Hangman @enigma="getEnigma" v-if="enigma == 0 && era == 'Victorienne'" :era="era"/>
      <Enigma1 @enigma="getEnigma" v-if="enigma == 1" :era="era" />
      <Enigma2 v-if="enigma == 2" :era="era" />
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
      enigma: 0
    }
  },
  methods: {
    changeEra() {
      if(this.era == 'Victorienne') {
        this.era = 'Années 60'
      } else if(this.era == 'Années 60') {
        this.era = 'Futur'
      } else if(this.era == 'Futur'){
        this.era = 'Victorienne'
      }
    },
    getEnigma(value) {
      this.enigma = value
    }
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

.era {
  height: 10vh;
}
</style>
