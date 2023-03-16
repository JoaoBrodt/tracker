<template>
  <section>
    <strong class="display">{{ timeFinal }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Cronometro",
  props: {
    time: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    timeFinal(): string {
      return new Date(this.time * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style>
.display {
  color: var(--texto-primario);
}
</style>
