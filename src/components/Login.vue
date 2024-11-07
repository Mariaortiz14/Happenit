<template>
  <div class="login-background">
    <div class="login-container">
      <h1>Iniciar Sesión</h1>
      <form @submit.prevent="handleLogin">
        <div>
          <label for="email">Correo electrónico:</label>
          <input v-model="username" type="email" id="email" required />
        </div>
        <div>
          <label for="password">Contraseña:</label>
          <input v-model="password" type="password" id="password" required />
        </div>
        <button type="submit">Iniciar Sesión</button>
      </form>
      <p>¿No tienes una cuenta? 
        <a @click="goToRegister">Regístrate aquí</a>
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Login',
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    async handleLogin() {
      try {
        const response = await axios.post('http://localhost:8000/login/', {
          username: this.username,
          password: this.password
        });
        if (response.data.message === 'Inicio de sesión exitoso') {
          this.$router.push('/home');  // Redirigir al Home tras inicio exitoso
        } else {
          alert('Usuario o contraseña incorrectos');
        }
      } catch (error) {
        alert('Error en el inicio de sesión');
      }
    },
    goToRegister() {
      this.$router.push('/register');  // Redirigir al formulario de registro
    }
  }
};
</script>

<style>
html, body {
  height: 100%;
  margin: 0;
}

.login-background {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; 
  background: url('src/assets/WhatsApp Image 2024-10-21 at 9.27.20 PM.jpeg') no-repeat center center;
  background-size: cover; 
}

.login-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: rgba(242, 242, 242, 0.9); 
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

form {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
}

input {
  margin-bottom: 15px;
  padding: 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

button {
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

p {
  margin-top: 10px;
}

a {
  color: #4CAF50;
  cursor: pointer;
}

a:hover {
  color: #45a049;
}
</style>
