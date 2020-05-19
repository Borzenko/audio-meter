<template>
  <div>
    <div>
      quality {{ quality }}
    </div>
    <div>
      volume {{ volume }}
    </div>
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

<style>
  .quality-5 > div {
    background: red;
  }

  .quality-3 > div, .quality-4 > div {
    background: orange;
  }

  .quality-1 > div, .quality-2 > div {
    background: green
  }

  .audio-meter {
    display: flex;
    width: 10px;
    height: 16px;
    align-items: center;
    justify-content: flex-start;
  }

  .audio-meter > div {
    width: 2px;
    border-radius: 15px;
    margin-right: 2px;
    min-height: 2px;
  }

  .audio-meter > div:last-child {
    margin-right: 0;
  }

  .quality-6 {
    width: 100% !important;
    height: 2px;
    border-radius: 15px;
    background: red;
  }
</style>
