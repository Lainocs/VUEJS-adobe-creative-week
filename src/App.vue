<template>

  <Hangman @enigma="getEnigma" v-if="enigma == 0 && era == 'Victorienne'" :era="era"/>

  <Enigma1 @enigma="getEnigma" v-if="enigma == 1" :era="era" />
  <Enigma2 v-if="enigma == 2" :era="era" />

  
  <div>
    {{era}}
    <button @click="changeEra">CHANGER D'EPOQUE</button>
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
