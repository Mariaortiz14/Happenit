<template>
    <div>
      <h1>Eventos</h1>
      <ul>
        <li v-for="event in events" :key="event.id">
          {{ event.name }} - {{ event.date }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        events: [
          { id: 1, name: "Evento 1", date: "2024-09-15" },
          { id: 2, name: "Evento 2", date: "2024-10-01" },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  h1 {
    font-size: 24px;
    color: #333;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    padding: 10px;
    border: 1px solid #ddd;
    margin-bottom: 5px;
  }
  </style>
