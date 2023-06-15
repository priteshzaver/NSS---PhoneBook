<script setup>
const props = defineProps(['contact'])
</script>

<template>
  <div>
    {{ props.contact.firstName }}
  </div>
</template>

<style scoped></style>
