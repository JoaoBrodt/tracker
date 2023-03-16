<template>
  <div class="is-flex is-align-itens-center is-justify-content-space-between">
    <Cronometro :time="time" />
    <button class="button" @click="start" :disabled="ativado">
      <!-- disativado=false  funciona -->
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>Começar</span>
    </button>
    <button class="button" @click="stop" :disabled="!ativado">
      <!-- disativado = true  não funciona -->
      <span class="icon"> <i class="fas fa-stop"></i></span>
      <span>Parar</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";
export default defineComponent({
  name: "Temporizador",
  emits: ["endTime"],
  data() {
    return {
      time: 0,
      cronometro: 0,
      ativado: false,
    };
  },
  methods: {
    start() {
      this.cronometro = setInterval(() => {
        this.time += 1;
      }, 1000);
      this.ativado = true;
    },
    stop() {
      clearInterval(this.cronometro);
      this.ativado = false;
      this.$emit("endTime", this.time);
      this.time = 0;
    },
  },
  components: { Cronometro },
});
</script>
