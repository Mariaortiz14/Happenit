<template>
  <div>
    <Header />
    <h1>Bienvenido {{ user.name }}</h1>
    <Calendar />
    <EventList />
    <Footer />
  </div>
</template>

<script>
import Header from './Header.vue'
import Footer from './Footer.vue'
import Calendar from './Calendar.vue'
import EventList from './EventList.vue'

export default {
  data() {
    return {
      user: { name: '' } // Asumimos que el nombre del usuario será traído tras el inicio de sesión
    }
  },
  mounted() {
    const loggedUser = JSON.parse(localStorage.getItem('user'))
    if (loggedUser) {
      this.user = loggedUser
    } else {
      this.$router.push('/login')
    }
  }
}
</script>
