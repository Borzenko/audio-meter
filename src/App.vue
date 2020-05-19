<template>
  <div id="app">
    <audio-meter
      :quality="quality"
      :volume="volume"
    />
  </div>
</template>

<script>
import AudioMeter from './components/AudioMeter.vue';

export default {
  name: 'App',
  components: {
    AudioMeter,
  },
  data() {
    return {
      quality: 1,
      volume: 0,
    };
  },
  methods: {
    getRandomInt(m, mx) {
      const min = Math.ceil(m);
      const max = Math.floor(mx);
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
  },
  mounted() {
    setInterval(() => {
      this.quality = this.getRandomInt(1, 6);
      this.volume = (Math.random()).toFixed(1);
    }, 500);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
