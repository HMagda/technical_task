<template>
  <div class="navbar-wrapper">
    <div class="logo-container"></div>
    <nav>
      <button @click="navigateTo('start')">Start</button>
      <button @click="navigateTo('about-me')">O Mnie</button>
      <button @click="navigateTo('gallery')">Galeria</button>
      <button @click="openContactModal">Kontakt</button>
    </nav>
    <div class="social-icons-container">
      <button class="facebook social-icon"></button>
      <button class="instagram social-icon"></button>
      <button class="youtube social-icon"></button>
    </div>
  </div>
</template>

<script lang="ts">
import './NavigationMenu.scss'
import { defineComponent } from 'vue'

export default defineComponent({
  methods: {
    navigateTo(section: string) {
      this.$emit('navigateTo', section)
    },
    openContactModal() {
      this.$emit('openContactModal')
    }
  }
})
</script>
