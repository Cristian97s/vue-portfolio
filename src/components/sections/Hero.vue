<script setup>
</script>

<template>
  <section class="hero">

    <div class="hero-content">

      <div class="hero-left">
        <span class="year">2026</span>
        <h1 class="title">
          Cuando el reloj marca la medianoche… <br/> comienza la Hora Oscura.
        </h1>

        <div class="buttons">
          <a href="#" class="btn-primary">Personajes</a>
          <a href="#" class="btn-link">Soundtrack</a>
        </div>
      </div>

      <div class="hero-right">
        <img src="../../assets/makoto-sleep-Photoroom.png" alt="Cristian">
      </div>

    </div>

  </section>
</template>

<style scoped>
.hero {
  height: 100vh;
  position: relative;
  overflow: hidden;
  color: white;
}

/* Fondo dividido diagonal */
.hero::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background: linear-gradient(120deg,
      rgba(18, 29, 64) 50%,
      rgba(4, 63, 140) 50%);
  z-index: -1;
}

/* CONTENIDO PRINCIPAL */
.hero-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  padding: 0 80px;
}

.hero-left {
  flex: 1;
}

.year {
  font-size: 1.2rem;
  opacity: 0.7;
}

.title {
  font-size: 3rem;
  line-height: 1.1;
  margin: 20px 0;
}

.buttons {
  display: flex;
  gap: 20px;
  margin-top: 30px;
}

.btn-primary {
  background: white;
  color: black;
  padding: 12px 30px;
  text-decoration: none;
  border-radius: 5px;
  font-weight: bold;
}

.btn-link {
  color: white;
  text-decoration: none;
  border-bottom: 1px solid white;
  padding-bottom: 4px;
}

/* Imagen derecha */
.hero-right {
  flex: 1;
  display: flex;
  justify-content: center;
}

.hero-right img {
  width: 80%;
  height: 100%;
  object-fit: cover;
}
</style>