<script setup lang="ts">
import type { Event } from '@/type';
defineProps<{
  event: Event
}>()
</script>
<template>
    <div class="category-organizer">
      <span>{{ event.category }}</span> |
      <span>{{ event.organizer }}</span>
    </div>
  </template>
  
  <style scoped>
  .category-organizer {
    text-align: right;
    font-size: 16px;
  }
  </style>