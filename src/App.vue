<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-mode': modoEscuro }"
  >
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefas" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
        <Box v-if="listaEstaVazia"> Nada para mostrar ainda! </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Box from "./components/Box.vue";
import Formulario from "./components/Formulario.vue";
import Tarefa from "./components/Tarefa.vue";
import ITarefa from "./interfaces/ITarefa";

export default defineComponent({
  name: "App",
  components: { BarraLateral, Formulario, Tarefa, Box },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false,
    };
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    },
  },
  methods: {
    salvarTarefas(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema() {
      this.modoEscuro = !this.modoEscuro;
    },
  },
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
  --bg-lateral: #dc5c54;
  --bg-tarefa: #ecc354;
}
main.dark-mode {
  --bg-primario: #101b20;
  --texto-primario: #ddd;
  --bg-lateral: #6c2c24;
  --bg-tarefa: #89680f;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
