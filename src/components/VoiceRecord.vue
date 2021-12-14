<template>
  <div class="voice-record">
    <VueRecord
      class="voice-record--record"
      @error="error = $event"
      @result="onResult"
    >
      <div v-html="icons.play"></div>

      <template slot="isInitiating">
        <div v-html="icons.play"></div>
      </template>

      <template slot="isRecording">
        <div v-html="icons.stop"></div>
      </template>
    </VueRecord>

    <span v-if="error" class="voice-record--error">{{ error }}</span>
    <audio class="voice-record--player" ref="player" controls></audio>
  </div>
</template>

<script>
import VueRecord from "@loquiry/vue-record-audio";

export default {
  name: "VoiceRecord",
  components: { VueRecord },
  data() {
    return {
      error: null,
      icons: {
        play: '<svg width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M19.643 12.848a1 1 0 0 0 0-1.696L6.53 2.956A1 1 0 0 0 5 3.804v16.392a1 1 0 0 0 1.53.848l13.113-8.196Z" fill="#fff"/></svg>',
        stop: '<svg width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M6 6h12v12H6V6Z" fill="#fff"/></svg>',
        permission:
          '<svg width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M3 16h2v6a1 1 0 1 1-2 0v-6ZM11 13h2v9a1 1 0 1 1-2 0v-9ZM3 2a1 1 0 0 1 2 0v9H3V2ZM19 16h2v6a1 1 0 1 1-2 0v-6ZM19 2a1 1 0 1 1 2 0v9h-2V2ZM11 2a1 1 0 1 1 2 0v6h-2V2Z" fill="#fff"/><rect x="16" y="13" width="8" height="5" rx="2" fill="#fff"/><rect x="8" y="6" width="8" height="5" rx="2" fill="#fff"/><rect y="13" width="8" height="5" rx="2" fill="#fff"/></svg>',
      },
    };
  },
  methods: {
    onResult(data) {
      this.$refs.player.src = URL.createObjectURL(data.blob);
    },
  },
};
</script>

<style scoped>
.voice-record--record {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  border: none;
  outline: none;
  background-color: #4db6ac;
}

.voice-record--record.active {
  background-color: #fd2822;
}

.voice-record--player {
  display: block;
  padding-top: 30px;
  margin: 0 auto;
}
</style>
