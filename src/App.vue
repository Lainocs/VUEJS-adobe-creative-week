<template>
  <div class="screen">
    <div v-if="game == false">

        <div v-if="startMenu">

          <StartMenu />
          <button class="start-button" @click="startGame()"> Lance le jeu ! </button>

        </div>


        <div v-if="endMenu">

          <EndMenu />

        </div>


    </div>
    <div v-else>
      <div id="content">
        <div class="era-title">{{era}}</div>
        <div @click="clicked1" class="border-enigma-1" v-if="enigma == 0 && era == 'Époque victorienne' && border1 == true"></div>
        <Hangman @enigma="getEnigma" v-if="enigma == 0 && view1 == true && era == 'Époque victorienne' && border1 == false" :era="era"/>
        
        <img class="numbers-60" v-if="era == 'Années 60'" :src="numbers60" alt="numbers-60">
        
        <div @click="clicked2" class="border-enigma-2" v-if="enigma == 1 && era == 'Époque victorienne' && border2 == true"></div>
        <Enigma1 @enigma="getEnigma" v-if="enigma == 1 && view2 == true" :era="era" />

        <img v-if="enigma == 2" :src="bijoux" alt="bijoux" style="width: 500px; height: auto;">

        <div @click="clicked3" class="border-enigma-3" v-if="enigma == 2 && era == 'Années 60' && border3 == true"></div>
        <Enigma2 @enigma="getEnigma" v-if="enigma == 2 && view3 == true" :era="era" />

        <img class="key" v-if="enigma == 3" :src="key" alt="key">

        <div @click="clicked4" class="border-enigma-4" v-if="enigma == 3 && era == 'Années 60' && border4 == true"></div>

      </div>
      <div class="era">
        <button @click="changeEra">Changer d'époque</button>
      </div>

      <div class="inventory">
        
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
      numbers60: "https://github.com/Lainocs/adobe-creative-week/blob/main/src/assets/chiffres_60.png?raw=true",
      game: false,
      startMenu: true,
      endMenu: false,

      bijoux: "https://github.com/Lainocs/adobe-creative-week/blob/main/src/assets/bijoux_interieur.png?raw=true",
      key: "https://github.com/Lainocs/adobe-creative-week/blob/lucas/src/assets/victorian_key.png?raw=true",

      era: 'Époque victorienne',
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
        document.getElementById("app").style.backgroundImage = "url('https://github.com/Lainocs/adobe-creative-week/blob/lucas/src/assets/victorienne.png?raw=true')";
        this.game = true
        this.startMenu = false
    },
    changeEra() {
      if(this.era == 'Époque victorienne') {
        this.era = 'Années 60'
        document.getElementById("app").style.backgroundImage = "url('https://github.com/Lainocs/adobe-creative-week/blob/main/src/assets/60.png?raw=true')";
      } else if(this.era == 'Années 60') {
        this.era = 'Époque victorienne'
        document.getElementById("app").style.backgroundImage = "url('https://github.com/Lainocs/adobe-creative-week/blob/lucas/src/assets/victorienne.png?raw=true')";
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
      document.getElementById("app").style.backgroundImage = "url('https://github.com/Lainocs/adobe-creative-week/blob/main/src/assets/mordern_room.png?raw=true')";
      this.game = false
      this.endMenu = true
    },
  },
}
</script>

<style>
@font-face {
  font-family: 'headline_font';
  src: local('headline_font'), url('assets/fonts/Academy_Engraved_LET.ttf') format('truetype');
}
@font-face {
  font-family: 'body_font';
  src: local('body_font'), url('assets/fonts/Athelas-Regular.woff') format('woff');
}
@font-face {
  font-family: 'body_font';
  src: local('body_font'), url('assets/fonts/Athelas-Bold.woff') format('woff');
  font-weight: bold;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h1 {
  font-size: 30px;
  margin-bottom: 30px;
  text-shadow: 2px 2px 2px #44371a;
  font-family: "body_font";
  font-weight: bold;
}

h2 {
  font-size: 24px;
  color: #44371a;
  text-shadow: 1px 1px 2px #44371a;
  font-family: "body_font";
  font-weight: bold;
}

#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  background-image: url('https://github.com/Lainocs/adobe-creative-week/blob/main/src/assets/mordern_room.png?raw=true');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: bottom;
  background-attachment: fixed;
  font-family: "body_font";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
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
  padding: 30px 50px;
  background: rgba(94, 85, 67, 0.164);
  box-shadow: 1px 1px 5px rgb(77, 77, 77);
  border: none;
  border-radius: 5px;
  color: rgba(255, 255, 255, 0.39);
  font-family: "body_font";
  font-size: 30px;
  font-weight: bold;
  animation: ease-in-out;
  transition: 0.5s;
}
.start-button:hover {
  background: rgba(94, 85, 67, 0.63);
  border: none;
  color: white;
  font-family: "body_font";
  font-size: 32px;
  font-weight: bold;
  padding: 30px 50px
}

#content {
  min-height: 80vh;
}

.numbers-60 {
  position: absolute;
  top: 350px;
  left: 480px;
  width: 10px;
  height: auto;
}

.border-enigma-1 {
  cursor: pointer;
  position: absolute;
  left: 230px;
  bottom: 70px;
  margin: 100px 0;
  width: 80px;
  height: 80px;
}

.border-enigma-2 {
  cursor: pointer;
  position: absolute;
  left: 500px;
  top: 90px;
  margin: 100px 0;
  width: 30px;
  height: 60px;
}

.border-enigma-3 {
  cursor: pointer;
  position: absolute;
  right: 400px;
  bottom: 50px;
  margin: 100px 0;
  width: 90px;
  height: 50px;
}
.border-enigma-4 {
  cursor: pointer;
  position: absolute;
  right: 20px;
  bottom: 30px;
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

.key {
  position: absolute;
  width: 100px;
  height: auto;
  right: 50px;
  top: 50px;
}

.era-title {
  margin: 0 auto;
  width: 50vw;
  color: rgb(253, 253, 253);
  background-color: rgba(129, 95, 1, 0.397);
  padding: 10px;
  font-size: 24px;
  font-weight: bold;
}

.era button {
  cursor: pointer;
  color: white;
  border: none;
  border-radius: 5px;
  background-color: #432E00;
  padding: 10px 20px;
  font-size: 24px;
  font-family: "body_font";
  font-weight: bold;
  transition: 0.3s;
}
.era button:hover {
  background-color: #5e4000;
  box-shadow: 1px 1px 5px rgb(29, 17, 0);
  font-size: 25px;

}

</style>
