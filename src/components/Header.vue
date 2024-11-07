<template>
  <header>
  <!--  <nav>
      <img src="src\assets\logo-happenit.jpeg" alt="happenit-logo.jpeg" />
      <ul>
        <li><router-link to="/">Inicio</router-link></li>
        <li><router-link to="/login" @click="logout">Cerrar sesión</router-link></li>
      </ul>
    </nav>-->
  </header>
</template>

<script>
export default {
  methods: {
    logout() {
      localStorage.removeItem('user')
      this.$router.push('/login')
    }
  }
}
</script>

<style>
/* Estilos para el header */
header {
  background-color: #333;
  padding: 10px 20px;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav img {
  max-width: 150px;
}

ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

ul li {
  display: inline;
}

ul li a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

ul li a:hover {
  color: #4CAF50;
}

/* Adaptación a pantallas pequeñas */
@media (max-width: 768px) {
  nav {
    flex-direction: column;
    align-items: flex-start;
  }

  ul {
    flex-direction: column;
    gap: 10px;
  }

  nav img {
    margin-bottom: 10px;
  }
}
</style>
