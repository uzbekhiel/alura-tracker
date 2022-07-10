<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <barra-lateral />
    </div>
    <div class="column is-three-quarter">
      <formulario @tarefaFinalizada="cadastrarTarefa($event)" />
      <div class="lista" v-if="!listaVazia">
        <tarefa v-for="(tarefa, i) in tarefas" :key="i" :tarefa="tarefa" />
      </div>
      <box class="no-data" v-else>
        <span> Não existem tarefas cadastradas </span>
      </box>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import barraLateral from "./components/barra-lateral.vue";
import Box from "./components/box.vue";
import Formulario from "./components/formulario.vue";
import Tarefa from "./components/tarefa.vue";
import iTarefa from "./interface/ITarefa";

export default defineComponent({
  components: { barraLateral, Formulario, Tarefa, Box },
  name: "App",
  data() {
    return {
      tarefas: [] as iTarefa[],
    };
  },
  computed: {
    listaVazia(): boolean {
      return this.tarefas.length === 0;
    },
  },
  methods: {
    cadastrarTarefa(e: iTarefa): void {
      console.log(e);
      this.tarefas.push(e);
    },
  },
});
</script>

<style scoped>
.lista {
  padding: 1.5rem;
}
.no-data {
  margin: 1.5rem;
}
</style>
