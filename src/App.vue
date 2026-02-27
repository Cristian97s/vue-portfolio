<script setup>
import Navbar from './components/layout/Navbar.vue';
import Hero from './components/sections/Hero.vue';
import Skills from './components/sections/Skills.vue';
import Experience from './components/sections/Experience.vue';
import Projects from './components/sections/Projects.vue';
import Contact from './components/sections/Contact.vue';
import AboutMe from './components/sections/AboutMe.vue';
</script>

<template>
  <Navbar />
  <main>
    <Hero />
    <AboutMe />
    <Skills />
    <Projects />
    <Experience />
    <Contact />
  </main>
</template>

<style scoped></style>
