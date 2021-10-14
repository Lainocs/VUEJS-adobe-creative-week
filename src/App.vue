<template>
  <div class="screen">
    <div v-if="game == false">

        <div v-if="startMenu">

          <StartMenu />
          <button class="start-button" @click="startGame()">START</button>

        </div>


        <div v-if="endMenu">

          <EndMenu />

        </div>


    </div>
    <div v-else>
      <div id="content">
        <div class="era-title">{{era}}</div>
        {{enigma}}
        <div @click="clicked1" class="border-enigma-1" v-if="enigma == 0 && era == 'Victorienne' && border1 == true"></div>
        <Hangman @enigma="getEnigma" v-if="enigma == 0 && view1 == true && era == 'Victorienne' && border1 == false" :era="era"/>

        <div @click="clicked2" class="border-enigma-2" v-if="enigma == 1 && era == 'Victorienne' && border2 == true"></div>
        <Enigma1 @enigma="getEnigma" v-if="enigma == 1 && view2 == true" :era="era" />

        <img v-if="enigma == 2" :src="bijoux" alt="bijoux" style="width: 500px; height: auto;">

        <div @click="clicked3" class="border-enigma-3" v-if="enigma == 2 && era == 'Années 60' && border3 == true"></div>
        <Enigma2 @enigma="getEnigma" v-if="enigma == 2 && view3 == true" :era="era" />

        <img v-if="enigma == 3" :src="key" alt="key" style="width: 500px; height: auto;">

        <div @click="clicked4" class="border-enigma-4" v-if="enigma == 3 && era == 'Années 60' && border4 == true"></div>

      </div>
      <div class="era">
        <button @click="changeEra">Voyager dans le temps</button>
      </div>
    </div>
  </div>
  
</template>

<script>
import Enigma1 from './components/Enigma1.vue'
import Enigma2 from './components/Enigma2.vue'
import Hangman from './components/Hangman.vue'
import StartMenu from './components/StartMenu.vue'
import EndMenu from './components/EndMenu.vue'

export default {
  name: 'App',

  components: {
    StartMenu,
    EndMenu,
    Hangman,
    Enigma1,
    Enigma2,
  },
  data() {
    return {
      game: false,
      startMenu: true,
      endMenu: false,

      bijoux: "/img/bijoux.7b77d87b.jpeg",
      key: "",

      era: 'Victorienne',
      enigma: 0,

      border1: true,
      view1: false,

      border2: true,
      view2: false,

      border3: true,
      view3: false,

      border4: true,
    }
  },
  methods: {

    startGame() {
        document.getElementById("app").style.backgroundImage = "url('/img/musee.5735396c.jpg')";
        this.game = true
        this.startMenu = false
    },
    changeEra() {
      if(this.era == 'Victorienne') {
        this.era = 'Années 60'
        document.getElementById("app").style.backgroundImage = "url('/img/60.7827e09b.jpg')";
      } else if(this.era == 'Années 60') {
        this.era = 'Victorienne'
        document.getElementById("app").style.backgroundImage = "url('/img/musee.5735396c.jpg')";
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
    clicked4() {
      this.border3 = false
      document.getElementById("app").style.backgroundImage = "url('/img/salon.5d04a135.jpg')";
      this.game = false
      this.endMenu = true
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
  background-image: url('assets/salon.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: bottom;
  background-attachment: fixed;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.screen {
  height: 100vh;
  width: 100vw;
  flex-direction: column;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

.start-button {
  width: 10vw;
  height: 10vh;
}

#content {
  min-height: 80vh;
}

.border-enigma-1 {
  cursor: pointer;
  position: absolute;
  right: 580px;
  bottom: 150px;
  border: 2px solid black;
  margin: 100px 0;
  width: 80px;
  height: 80px;
}

.border-enigma-2 {
  cursor: pointer;
  position: absolute;
  left: 370px;
  bottom: -20px;
  border: 2px solid black;
  margin: 100px 0;
  width: 80px;
  height: 50px;
}

.border-enigma-3 {
  cursor: pointer;
  position: absolute;
  right: 360px;
  bottom: 50px;
  border: 2px solid black;
  margin: 100px 0;
  width: 90px;
  height: 50px;
}
.border-enigma-4 {
  cursor: pointer;
  position: absolute;
  right: 20px;
  bottom: 30px;
  border: 2px solid black;
  margin: 100px 0;
  width: 200px;
  height: 400px;
}

.era {
  height: 10vh;
  width: 40vw;
  margin: 0 auto;
  display: flex;
  justify-content: space-around;
}

.era-title {
  width: 50vw;
  color: black;
  background-color: aliceblue;
  padding: 10px 30px;
}

.era button {
  cursor: pointer;
  color: black;
  border-radius: 5px;
  background-color: aliceblue;
  padding: 20px;
}
.era button:hover {
  background-color: rgb(226, 233, 240);
}

</style>
