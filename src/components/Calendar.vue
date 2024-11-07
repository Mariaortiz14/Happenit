<template>
  <div>
    <h2>Calendario de eventos</h2>
    <div class="calendar">
      <!-- Aquí va la implementación del calendario -->
      <p>Calendario en construcción</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      events: [] // Este array almacenará los eventos para mostrar en el calendario
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
/* Añadir estilos del calendario aquí */
</style>

  