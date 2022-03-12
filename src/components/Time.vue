<template>
  <div class="time">
    {{sec2min(time)["min"]}}:{{sec2min(time)["sec"]}}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    time: Number
  },
  methods: {
  sec2min(time) {
    var min = Math.floor(time / 60);
    var sec = time % 60;

    return {
      min: min,
      sec: sec
    }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
