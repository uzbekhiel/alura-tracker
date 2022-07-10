<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para a criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricaoTarefa"
        />
      </div>
      <div class="column">
        <temporizador
          @temporizadorFinalizado="finalizado($event)"
          :descricaoFeita="descricaoTarefa !== ''"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import iTarefa from "@/interface/ITarefa";
import { defineComponent } from "vue";
import temporizador from "./temporizador.vue";

export default defineComponent({
  components: { temporizador },
  name: "FormularioComponent",
  data() {
    return {
      descricaoTarefa: "",
    };
  },
  emits: ["tarefaFinalizada"],
  methods: {
    finalizado(e: any): void {
      const t: iTarefa = {
        descricao: this.descricaoTarefa,
        tempo: e,
      };
      this.$emit("tarefaFinalizada", t);
      this.descricaoTarefa = "";
    },
  },
});
</script>
