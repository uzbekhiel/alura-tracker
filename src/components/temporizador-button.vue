<template>
  <button
    class="button"
    @click="$emit('clicked', $event)"
    :disabled="isDisabled"
  >
    <span class="icon">
      <i class="fas" :class="icon"></i>
    </span>
    <span>{{ name }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TemporizadorButton",
  props: {
    name: {
      type: String,
      default: "NomeBotão",
    },
    isDisabled: {
      type: Boolean,
    },
    icon: {
      type: String,
    },
  },
  emits: ["clicked"],
});
</script>


<style>
</style>