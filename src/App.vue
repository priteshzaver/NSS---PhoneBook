<script setup>
import { ref } from 'vue'
import ContactForm from './components/ContactForm.vue'
import ContactList from './components/ContactList.vue'
import sampleData from './sampleData'

const contacts = ref(sampleData)
</script>

<template>
  <h1 class="is-size-1 has-text-centered has-text-info">Vue Phonebook</h1>
  <div class="container px-4">
    <div class="columns">
      <div class="column">
        <ContactForm />
      </div>
      <div class="column">
        <ContactList />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
