<template>
  <nav>
    <button @click="navigateTo('start')">Start</button>
    <button @click="navigateTo('about-me')">O Mnie</button>
    <button @click="navigateTo('gallery')">Galeria</button>
    <button @click="openContactModal">Kontakt</button>
  </nav>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  methods: {
    navigateTo(section: string) {
      this.$emit('navigateTo', section);
    },
    openContactModal() {
      this.$emit('openContactModal');
    },
  },
});
</script>
