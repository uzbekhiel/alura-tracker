<template>
  <box>
    <div class="columns">
      <div class="column is-7">{{ tarefa.descricao }}</div>
      <div class="column">
        <cronometro :tempoEmSegundos="tarefa.tempo" />
      </div>
    </div>
  </box>
</template>

<script lang="ts">
import iTarefa from "@/interface/ITarefa";
import { defineComponent, PropType } from "vue";
import Box from "./box.vue";
import cronometro from "./cronometro.vue";

export default defineComponent({
  components: { cronometro, Box },
  name: "TarefaComponent",
  props: {
    tarefa: {
      type: Object as PropType<iTarefa>,
      required: true,
    },
  },
});
</script>

<style scoped>
</style>