<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Time :time="time_sec" />
  <button v-on:click="startTimer" >start</button>
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
      time_sec: 1801

    }
  },
  methods: {
     countdown: function() {
      if (this.time_sec >= 1) {
        this.time_sec--;
      }
    },
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
    },
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
