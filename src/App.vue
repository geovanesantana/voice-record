<template>
  <div id="app">
    <h1>Hi there!</h1>

    <img
      alt="voice record"
      src="./assets/voice-record-image.png"
      width="200px"
    />

    <p>
      Welcome to Voice Record, <br />
      press the button to record an audio.
    </p>

    <VoiceRecord />
  </div>
</template>

<script>
import VoiceRecord from "./components/VoiceRecord.vue";

export default {
  name: "App",
  components: {
    VoiceRecord,
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
  margin-top: 60px;
}
</style>
