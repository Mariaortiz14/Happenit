<template>
  <div>
    <h2>Próximos eventos</h2>
    <div class="event-list">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
  </div>
</template>

<script>
import EventCard from './EventCard.vue'

export default {
  components: { EventCard },
  data() {
    return {
      events: []
    }
  },
  mounted() {
    this.fetchEvents()
  },
  methods: {
    fetchEvents() {
      fetch('http://localhost:8000/events')
        .then(response => response.json())
        .then(data => {
          this.events = data
        })
        .catch(error => console.log(error))
    }
  }
}
</script>

<style>
.event-list {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
