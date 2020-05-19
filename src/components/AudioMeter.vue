<template>
  <div>
    <div v-if="quality === 6" class="audio-meter">
      <div class="quality-6"></div>
    </div>
    <div v-else :class="'quality-' + quality" class="audio-meter">
      <div :style="{ 'height': `${volume * 10}px` }"></div>
      <div :style="{ 'height': `${volume * 16}px` }" v-if="quality < 5"></div>
      <div :style="{ 'height': `${volume * 10}px` }" v-if="quality === 1 || quality === 2"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    quality: {
      type: Number,
      default: 6,
    },
    volume: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style scoped>
  .quality-5 > div {
    background: #FF9D00;
  }

  .quality-3 > div, .quality-4 > div {
    background: #FF9D00;
  }

  .quality-1 > div, .quality-2 > div {
    background: #15FF00
  }

  .audio-meter {
    margin: 0 auto;
    display: flex;
    width: 10px;
    height: 16px;
    align-items: center;
    justify-content: center;
  }

  .audio-meter > div {
    width: 2px;
    border-radius: 4px;
    margin-right: 2px;
    min-height: 2px;
  }

  .audio-meter > div:last-child {
    margin-right: 0;
  }

  .quality-6 {
    width: 100% !important;
    height: 2px;
    border-radius: 4px;
    background: #FF0000;
  }
</style>
