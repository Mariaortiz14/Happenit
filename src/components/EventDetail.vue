<template>
    <div class="container">
      <h2>{{ event.title }}</h2>
      <p>{{ event.description }}</p>
      <button @click="goBack">Back to Events</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    props: ['id'],
    data() {
      return {
        event: {}
      };
    },
    async created() {
      try {
        const response = await axios.get(`http://localhost:8000/events/${this.id}`);
        this.event = response.data;
      } catch (error) {
        console.error('Failed to load event details', error);
      }
    },
    methods: {
      goBack() {
        this.$router.push('/events');
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 600px;
    margin: auto;
    padding: 1rem;
  }
  
  button {
    padding: 0.5rem 1rem;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  </style>
