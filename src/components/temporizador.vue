<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <cronometro :tempoEmSegundos="tempoEmSegundos" />
    <temporizador-button
      :icon="'fa-play'"
      :isDisabled="cronometroRodando || !descricaoFeita"
      :name="'play'"
      @clicked="iniciar"
    />
    <temporizador-button
      :icon="'fa-stop'"
      :isDisabled="!cronometroRodando"
      :name="'stop'"
      @clicked="finalizar"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import cronometro from "./cronometro.vue";
import TemporizadorButton from "./temporizador-button.vue";

export default defineComponent({
  components: { cronometro, TemporizadorButton },
  name: "TemporizadorComponent",
  emits: ["temporizadorFinalizado"],
  props: {
    descricaoFeita: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },
  methods: {
    iniciar() {
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      this.cronometroRodando = false;
      clearInterval(this.cronometro);
      this.$emit("temporizadorFinalizado", this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    },
  },
});
</script>


<style>
</style>