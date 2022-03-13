<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <cronometro :timeInSeconds="timeInSeconds" />
    <button class="button" @click="iniciar" :disabled="cronRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"

import Cronometro from "@/components/Cronometro.vue"

export default defineComponent({
  name: "Temporizador",
  emits: ['atTerminatedTime'],
  components: {
    Cronometro,
  },
  data() {
    return {
      timeInSeconds: 0,
      cronometro: 0,
      cronRunning: false
    };
  },
  methods: {
    // começar a contagem
    iniciar () {
      this.cronRunning = true
      this.cronometro = setInterval(() => {
        ++this.timeInSeconds
      }, 1000)
    },
    finalizar () {
        this.cronRunning = false
      clearInterval(this.cronometro)
      this.$emit('atTerminatedTime', this.timeInSeconds)
      this.timeInSeconds = 0
    },
  },
});
</script>
