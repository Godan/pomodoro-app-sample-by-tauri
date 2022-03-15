<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Time :time="time_sec" />
  <button v-if="timer == null" v-on:click="startTimer" >start</button>
  <button v-if="timer != null" v-on:click="stopTimer" >stop</button>
  <button v-on:click="nextTimer" >next</button>
  {{mode}}
</template>

<script>
import Time from './components/Time.vue'

export default {
  name: 'App',
  components: {
    Time
  },
  data: () => {
    return {
      time_sec: 1801,
      timer: null,
      mode: 'work',
      mode_type_list: {
        work: 25 * 60,
        rest: 5 * 60
      }

    } 
  },
  methods: {
     countdown: function() {
      if (this.time_sec >= 1) {
        this.time_sec--;
      }``
    },
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
    },
    stopTimer: function() {
      clearInterval(this.timer);
      this.timer = null;
    },
    nextTimer: function(){
      this.stopTimer();
      if(this.mode == "work"){
        this.time_sec = this.mode_type_list["rest"]
        this.mode = "rest"
      }
      else if (this.mode == "rest") {
        this.time_sec = this.mode_type_list["work"]
        this.mode = "work"
      }
    }
  }
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
