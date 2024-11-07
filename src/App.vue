<template>
  <div id="app">
    <router-view></router-view> 
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  background-color: #333;
  color: #fff;
  padding: 1rem;
  text-align: center;
}

main {
  flex: 1;
}
footer {
  background-color: #333;
  color: #fff;
  padding: 1rem;
  text-align: center;
}
.event-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}

.event-list .event-card {
  flex: 1 1 300px;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.event-list {
  display: flex;
  flex-wrap: wrap;
}

#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  padding: 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
}

button {
  margin: 10px;
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

form {
  margin: 20px 0;
}

input {
  padding: 10px;
  margin: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

h2 {
  margin-top: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 10px 0;
  font-size: 18px;
}
</style>

