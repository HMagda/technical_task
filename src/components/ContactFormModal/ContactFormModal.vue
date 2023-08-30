<template>
  <div v-if="isOpen" class="form-wrapper">
    <form @submit.prevent="validateForm">
      <img
        class="close-btn"
        @click="$emit('closeModal')"
        src="../../assets/images/close.jpg"
        alt="Close"
      />
      <label class="input-label">IMIĘ<span class="red-asterisk">*</span></label>
      <input type="text" v-model="formData.name" placeholder="- wpisz -" />
      <label class="input-label">NAZWISKO <span class="red-asterisk">*</span></label>
      <input type="text" v-model="formData.surname" placeholder="- wpisz -" />
      <label class="input-label">ADRES E-MAIL<span class="red-asterisk">*</span></label>
      <input type="email" v-model="formData.email" placeholder="- wpisz -" />
      <p class="footnote"><span class="red-asterisk">*</span>-pola wymagane</p>
      <div class="accept-container">
        <input type="checkbox" class="custom-checkbox" v-model="formData.accept" />
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
          ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation
          ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </p>
      </div>
      <button type="submit">Wyślij</button>
      <p class="error" v-if="errorMessage">{{ errorMessage }}</p>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import './ContactFormModal.scss'

export default defineComponent({
  props: {
    isOpen: {
      type: Boolean,
      required: true
    }
  },
  emits: ['closeModal'],
  setup(props, { emit }) {
    const formData = ref({
      name: '',
      surname: '',
      email: '',
      accept: false
    })

    const errorMessage = ref('')

    const validateForm = () => {
      errorMessage.value = ''

      if (
        !formData.value.name ||
        !formData.value.surname ||
        !formData.value.email ||
        !formData.value.accept
      ) {
        errorMessage.value = 'Proszę uzupełnić wymagane pola!'
        return
      }
      console.log(JSON.stringify(formData.value))
      emit('closeModal')
    }

    return {
      formData,
      errorMessage,
      validateForm
    }
  }
})
</script>
