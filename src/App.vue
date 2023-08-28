<template>
  <div id="app">
    <NavigationMenu 
      @navigateTo="scrollToSection" 
      @openContactModal="openModal"
    />
    <div id="start" ref="startSection"><StartSection/></div>
    <div id="about-me" ref="aboutSection"><AboutSection /></div>
    <div id="gallery" ref="gallerySection"><ImageSlider /></div>
    <ContactFormModal :isOpen="isModalOpen" @closeModal="closeModal" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import NavigationMenu from './components/NavigationMenu.vue';
import StartSection from './components/StartSection.vue';
import AboutSection from './components/AboutSection.vue';
import ImageSlider from './components/ImageSlider.vue';
import ContactFormModal from './components/ContactFormModal.vue';

export default defineComponent({
  components: {
    NavigationMenu,
    StartSection,
    AboutSection,
    ImageSlider,
    ContactFormModal,
  },
  setup() {
    const isModalOpen = ref(false);

    const scrollToSection = (section: string) => {
      const element = document.getElementById(section);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    };

    const openModal = () => {
      isModalOpen.value = true;
    };

    const closeModal = () => {
      isModalOpen.value = false;
    };

    return {
      isModalOpen,
      scrollToSection,
      openModal,
      closeModal,
    };
  },
});
</script>