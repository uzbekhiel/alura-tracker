<template>
  <div class="box has-text-weight-bold">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BoxComponent",
});
</script>

<style scoped>
.box {
  background: rgba(49, 205, 140, 0.4);
}
</style>
