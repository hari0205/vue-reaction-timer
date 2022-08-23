<template>
    <h1>Reaction timer</h1>
    <button @click="startGame" class="Startbtn" :disabled="isPlaying" >Start</button>
    <Timer v-if="isPlaying" :delay="delay" @stop="endGame"/>
    <p v-if="showResult">Reaction Time : {{score}} ms</p>
</template>

<script>
 import Timer from './components/Timer.vue'

export default {
  
  components:{
    Timer
   
},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult : false,
    }
  },

  methods: {
    startGame(){
      this.delay = 1000 + Math.random() * 5500
      this.isPlaying = true
      
    },
    endGame(reaction){
      this.score= reaction
      this.isPlaying = false
      this.showResult= true
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


/* CSS */
.Startbtn {
  align-items: center;
  padding: 6px 14px;
  font-family: -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
  border-radius: 6px;
  color: #111111;
  background: rgb(255, 249, 249);
  border: none;
  box-shadow: 0px 0.5px 1px rgba(0, 0, 0, 0.1);
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.Startbtn:focus {
  box-shadow: 0px 0.5px 1px rgba(0, 0, 0, 0.1), 0px 0px 0px 3.5px rgba(58, 108, 217, 0.5);
  outline: 0;
}
</style>
