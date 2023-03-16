<template>
  <div class="box has-text-weight-bold" :style="estilo">
    <slot />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Box",
  data() {
    return {
      estilo: {
        background: "var(--bg-lateral)",
        color: "var(--texto-primario)",
      },
    };
  },
});
</script>
