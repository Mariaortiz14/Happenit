<template>
  <div class="event-card">
    <h3>{{ event.name }}</h3>
    <p>{{ event.description }}</p>
    <p><strong>Fecha:</strong> {{ new Date(event.date).toLocaleDateString() }}</p>
    <p><strong>Lugar:</strong> {{ event.location }}</p>
  </div>
</template>

<script>
export default {
  props: {
    event: Object
  }
}
</script>

<style>
.event-card {
  border: 1px solid #ccc;
  padding: 1rem;
  width: 200px;
}
</style>
