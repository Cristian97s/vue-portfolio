<!-- Navbar.vue -->
<script setup>
import { ref } from 'vue'

const isScrolled = ref(false)

window.addEventListener('scroll', () => {
  isScrolled.value = window.scrollY > 50
})
</script>

<template>
  <header class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container">
      <a href="#hero" class="logo">Inicio</a>
      <nav>
        <a href="#skills">Habilidades</a>
        <a href="#projects">Proyectos</a>
        <a href="#experience">Experiencia</a>
        <a href="#contact">Contacto</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  transition: all 0.4s ease;
  padding: 1.2rem 0;
}

.navbar.scrolled {
  background: rgba(10, 10, 20, 0.85);
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.logo {
  font-size: 1.6rem;
  font-weight: 700;
  color: #fff;
  text-decoration: none;
  letter-spacing: 1px;
}

nav a {
  margin-left: 2.5rem;
  color: #fff;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

nav a:hover {
  color: #fff;
  text-shadow: 0 0 8px rgba(255, 255, 255, 0.4);
}
</style>