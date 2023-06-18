<script setup>
import ContactListItem from './ContactListItem.vue'
import { computed, ref } from 'vue'
const props = defineProps(['contacts'])
const emit = defineEmits(['remove'])

const handleRemove = (email) => {
  emit('remove', email)
}

const searchQuery = ref('')
const searchedContact = computed(() => {
  return props.contacts.filter((contact) => {
    return (
      contact.firstName.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      contact.lastName.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      contact.email.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      contact.phoneNumber.includes(searchQuery.value)
    )
  })
})
</script>

<template>
  <div class="panel is-success">
    <div class="panel-heading">Contacts</div>
    <div>
      <input type="text" placeholder="Search" v-model="searchQuery" />
    </div>
    <div class="panel-block is-flex is-flex-direction-column is-align-items-stretch">
      <div v-for="contact in searchedContact" :key="contact.phoneNumber">
        <ContactListItem :contact="contact" @remove="handleRemove" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
