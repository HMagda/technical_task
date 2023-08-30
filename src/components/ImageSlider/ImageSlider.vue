<template>
  <div id="image-slider" class="slider-wrapper">
    <h1>Galeria</h1>
    <div class="slider">
      <div
        v-for="(image, index) in images"
        :key="index"
        class="slide"
        :class="{ 'active-slide': currentSlide === index }"
      >
        <img :src="isMobile ? image.mobile : image.desktop" alt="Slider Image" />
      </div>
    </div>
    <div class="slider-controls">
      <button @click="prevSlide" class="arrow prev-arrow">
        <img src="@/assets/images/arrow-left.jpg" alt="Previous" />
      </button>
      <button @click="nextSlide" class="arrow next-arrow">
        <img src="@/assets/images/arrow-right.jpg" alt="Next" />
      </button>
    </div>
    <div class="slider-dots">
      <button
        v-for="(image, index) in images"
        :key="index"
        @click="goToSlide(index)"
        :class="{ 'active-dot': currentSlide === index }"
        class="dot"
      ></button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import './ImageSlider.scss'

import beach from '@/assets/images/beach@2x.jpg'
import trees from '@/assets/images/trees@2x.jpg'
import car from '@/assets/images/car@2x.jpg'
import shoes from '@/assets/images/shoes@2x.jpg'

import beachMobile from '@/assets/images/beach.jpg'
import treesMobile from '@/assets/images/trees.jpg'
import carMobile from '@/assets/images/car.jpg'
import shoesMobile from '@/assets/images/shoes.jpg'

export default defineComponent({
  name: 'ImageSlider',
  setup() {
    const images = ref([
      { desktop: beach, mobile: beachMobile },
      { desktop: trees, mobile: treesMobile },
      { desktop: car, mobile: carMobile },
      { desktop: shoes, mobile: shoesMobile }
    ])

    const currentSlide = ref(0)

    const isMobile = ref(window.innerWidth <= 768)

    function nextSlide() {
      currentSlide.value = (currentSlide.value + 1) % images.value.length
    }

    function prevSlide() {
      currentSlide.value = (currentSlide.value - 1 + images.value.length) % images.value.length
    }

    function goToSlide(index: number) {
      currentSlide.value = index
    }

    return {
      images,
      currentSlide,
      isMobile,
      nextSlide,
      prevSlide,
      goToSlide
    }
  }
})
</script>
