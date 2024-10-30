<script setup lang="ts">
import EventCategoryOrganizer from '@/components/EventCategoryOrganizer.vue';
import EventCard from '@/components/EventCard.vue'
import type { Event } from '@/type'
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'

const events = ref<Event[]>()

onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
<h1>Events For Good</h1>
  <!-- new element -->
<div class="events">
  <div v-for="event in events" :key="event.id" class="eventcontainer">
      <EventCard :event="event" />
      <EventCategoryOrganizer :event="event" category="event.category" :organizer="event.organizer" />
  </div>
</div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.eventcontainer{
  display: flex;
  flex-direction: row; /* 使内容水平排列 */
  justify-content: space-between; /* 使内容两端对齐 */
  width: 100%; /* 根据需要调整宽度 */
  max-width: 600px; /* 设置最大宽度 */
  border: 1px solid #ccc; /* 可选：添加边框 */
  padding: 10px; /* 可选：添加内边距 */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* 可选：添加阴影 */
}
</style>
