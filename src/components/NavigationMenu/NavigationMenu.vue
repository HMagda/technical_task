<template>
  <div class="navbar-wrapper">
    <button class="menu-toggle" @click="toggleMenu">
      <img src="../../assets/images/hamburger.png" alt="Menu toggle" />
    </button>
    <div class="logo-container"></div>
    <nav :class="{ 'show-menu': showMenu, 'hide-menu': !showMenu }">
      <button @click="navigateTo('start')">Start</button>
      <button @click="navigateTo('about-me')">O Mnie</button>
      <button @click="navigateTo('gallery')">Galeria</button>
      <button @click="openContactModal">Kontakt</button>
    </nav>
    <div class="social-icons-container">
      <button @click="goToFacebook" class="facebook social-icon"></button>
      <button @click="goToInstagram" class="instagram social-icon"></button>
      <button @click="goToYouTube" class="youtube social-icon"></button>
    </div>
  </div>
</template>

<script lang="ts">
import './NavigationMenu.scss'
import { defineComponent, ref } from 'vue'

export default defineComponent({
  methods: {
    navigateTo(section: string) {
      this.$emit('navigateTo', section)
    },
    openContactModal() {
      this.$emit('openContactModal')
    },
    toggleMenu() {
      this.showMenu = !this.showMenu
    },
    goToFacebook() {
      window.open('https://www.facebook.com/', '_blank')
    },
    goToInstagram() {
      window.open('https://www.instagram.com/', '_blank')
    },
    goToYouTube() {
      window.open('https://www.youtube.com/', '_blank')
    }
  },
  setup() {
    const showMenu = ref(false)
    return { showMenu }
  }
})
</script>
