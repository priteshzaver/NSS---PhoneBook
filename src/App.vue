<script setup>
import { ref } from 'vue'
import ContactForm from './components/ContactForm.vue'
import ContactList from './components/ContactList.vue'

const contacts = ref(JSON.parse(localStorage.getItem('contacts')))

const setContactsInLocalStorage = () => {
  localStorage.setItem('contacts', JSON.stringify(contacts.value))
}

const addContact = (contact) => {
  contacts.value = [...contacts.value, contact]
  setContactsInLocalStorage()
}
const removeContact = (email) => {
  contacts.value = contacts.value.filter((contact) => contact.email !== email)
  setContactsInLocalStorage()
}
</script>

<template>
  <h1 class="is-size-1 has-text-centered has-text-info">Vue Phonebook</h1>
  <div class="container px-4">
    <div class="columns">
      <div class="column">
        <ContactForm @submit="addContact" />
      </div>
      <div class="column">
        <ContactList :contacts="contacts" @remove="removeContact" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
