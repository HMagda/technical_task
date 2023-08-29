<template>
    <div v-if="isOpen">
      <!-- Modal content with form -->
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  
  export default defineComponent({
    setup() {
      const isOpen = ref(false);
  
      const openModal = () => {
        isOpen.value = true;
      };
  
      const closeModal = () => {
        isOpen.value = false;
      };
  
      return {
        isOpen,
        openModal,
        closeModal,
      };
    },
  });
  </script>
  