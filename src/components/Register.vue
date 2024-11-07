<template>
  <div class="register">
    <div class="form-container">
      <h2>Registro</h2>
      <form @submit.prevent="registerUser" class="register-form">
        <input
          v-model="registerForm.name"
          type="text"
          placeholder="Nombre"
          required
          class="input-field"
        />
        <input
          v-model="registerForm.surname"
          type="text"
          placeholder="Apellido"
          class="input-field"
        />
        <input
          v-model="registerForm.phone"
          type="text"
          placeholder="Teléfono"
          required
          class="input-field"
        />
        <input
          v-model="registerForm.email"
          type="email"
          placeholder="Email"
          required
          class="input-field"
        />
        <div class="password-container">
          <input
            v-model="registerForm.password"
            :type="passwordVisible ? 'text' : 'password'"
            placeholder="Contraseña"
            required
            class="input-field"
          />
          <button type="button" @click="togglePasswordVisibility" class="eye-button">
            <span v-if="passwordVisible">👁️</span>
            <span v-else>👁️‍🗨️</span>
          </button>
        </div>
        <div class="password-container">
          <input
            v-model="registerForm.confirm_password"
            :type="confirmPasswordVisible ? 'text' : 'password'"
            placeholder="Repite tu contraseña"
            required
            class="input-field"
          />
          <button type="button" @click="toggleConfirmPasswordVisibility" class="eye-button">
            <span v-if="confirmPasswordVisible">👁️</span>
            <span v-else>👁️‍🗨️</span>
          </button>
        </div>
        <button type="submit" class="submit-button">Registrarse</button>
      </form>
      <p>
        ¿Ya tienes cuenta? <router-link to="/Login">Iniciar Sesión</router-link>
      </p>
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Swal from 'sweetalert2';

export default {
  data() {
    return {
      registerForm: {
        name: '',
        surname: '',
        phone: '',
        email: '',
        password: '',
        confirm_password: ''
      },
      passwordVisible: false,
      confirmPasswordVisible: false,
      errorMessage: ''
    };
  },
  methods: {
    togglePasswordVisibility() {
      this.passwordVisible = !this.passwordVisible;
    },
    toggleConfirmPasswordVisibility() {
      this.confirmPasswordVisible = !this.confirmPasswordVisible;
    },
    async registerUser() {
      try {
        if (this.registerForm.password !== this.registerForm.confirm_password) {
          this.errorMessage = "Las contraseñas no coinciden.";
          return;
        }

        const response = await axios.post('http://localhost:8000/users/', this.registerForm);
        Swal.fire('Éxito', 'Registro exitoso', 'success');
        
        // Redirigir al inicio de sesión tras registro exitoso
        this.$router.push('/Login');
      } catch (error) {
        this.errorMessage = error.response?.data?.detail || "Error al registrarse.";
        Swal.fire('Error', this.errorMessage, 'error');
      }
    }
  }
};
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
}

.register {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('src/assets/WhatsApp Image 2024-10-21 at 9.27.20 PM.jpeg') no-repeat center center;
  background-size: cover;
}

.form-container {
  max-width: 400px;
  padding: 20px;
  border-radius: 8px;
  background-color: rgba(255, 255, 255, 0.8);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

h2 {
  text-align: center;
  color: #333;
}

.register-form {
  display: flex;
  flex-direction: column;
}

.input-field {
  margin-bottom: 15px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  transition: border-color 0.3s;
}

.input-field:focus {
  border-color: #007bff;
  outline: none;
}

.password-container {
  position: relative;
}

.eye-button {
  position: absolute;
  right: 10px;
  top: 10px;
  background: none;
  border: none;
  cursor: pointer;
  color: #007bff;
  font-size: 20px;
}

.submit-button {
  padding: 10px;
  border: none;
  border-radius: 4px;
  background-color: #007bff;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  margin-top: 10px;
  text-align: center;
}
</style>
