<template>
  <header>
    <h1><img src="../assets/logo.png" alt="" /></h1>
    <button class="button" @click="alterarTema">{{ textButton }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "BarraLateral",
  data() {
    return {
      modoEscuro: false,
    };
  },
  computed: {
    textButton() {
      if (this.modoEscuro) {
        return "Desativar modo escuro";
      }
      return "Ativar Modo escuro";
    },
  },
  emits: ["aoTemaAlterado"],
  methods: {
    alterarTema() {
      this.modoEscuro = !this.modoEscuro;
      this.$emit("aoTemaAlterado");
    },
  },
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: var(--bg-lateral);
  width: 100%;
  height: 100vh;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
.button {
  width: 200px;
  background: var(--bg-fundo);
  color: var(--texto-primario);
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
