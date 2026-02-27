<script setup>
import { ref } from 'vue'

// Puedes mover esto a un archivo JSON o dejarlo aquí
const about = ref({
  name: 'Javier',
  role: 'Desarrollador Frontend | Especialista en Vue.js',
  headline: 'Construyo interfaces modernas, rápidas y con foco en la experiencia del usuario',
  location: 'Managua, Nicaragua',
  yearsExperience: '5+ años',
  mainTech: 'Vue 3, Nuxt, Pinia, TypeScript, Tailwind',
  bio: `
    Soy un desarrollador frontend apasionado por crear aplicaciones web intuitivas y de alto rendimiento. 
    Me enamoré de Vue.js en 2019 y desde entonces ha sido mi herramienta principal para casi todos mis proyectos personales y profesionales.
    
    Me motiva resolver problemas reales con código limpio, arquitectura escalable y un diseño que realmente se sienta bien al usarlo. 
    Disfruto especialmente trabajar en productos que impactan a muchas personas: e-commerce, dashboards, herramientas SaaS y aplicaciones educativas.
    
    Actualmente estoy enfocado en proyectos con Vue 3 + Composition API, Nuxt 3/4, y en incorporar más TypeScript y testing (Vitest + Playwright).
    
    Fuera del código me gusta el café nicaragüense fuerte, el fútbol, viajar cuando puedo y aprender constantemente (últimamente explorando un poco de Rust y Go por curiosidad).
  `,
  highlights: [
    { icon: '🚀', text: '5+ años trabajando con Vue.js' },
    { icon: '🌎', text: 'Proyectos entregados para clientes en LATAM y EE.UU.' },
    { icon: '🛠️', text: 'Especialista en rendimiento y accesibilidad web' },
    { icon: '📱', text: 'Experiencia mobile-first y PWA' },
    { icon: '🤝', text: 'Colaboración en equipos remotos y ágiles' }
  ],
  currentlyLooking: 'Busco oportunidades como Frontend Lead / Mid-Senior Vue Developer (remoto o híbrido en LATAM)'
})
</script>

<template>
  <section id="about" class="about-section">
    <div class="container">
      <div class="about-grid">
        <!-- Columna izquierda - Foto + datos rápidos -->
        <div class="about-photo-column">
          <div class="photo-wrapper">
            <!-- Cambia esta URL por tu foto real (subida a GitHub, Cloudinary, ImgBB, etc.) -->
            <img
              src="/src/assets/1762495282728.png"
              alt="Javier - Desarrollador Frontend"
              class="profile-photo"
            />
          </div>

          <div class="quick-info">
            <h1 class="name">{{ about.name }}</h1>
            <p class="role">{{ about.role }}</p>
            <p class="location">{{ about.location }}</p>
          </div>
        </div>

        <!-- Columna derecha - Contenido principal -->
        <div class="about-content">
          <h2 class="headline">{{ about.headline }}</h2>

          <div class="bio" v-html="about.bio.replace(/\n/g, '<br><br>')"></div>

          <div class="highlights">
            <div v-for="(item, i) in about.highlights" :key="i" class="highlight-item">
              <span class="highlight-icon">{{ item.icon }}</span>
              <span>{{ item.text }}</span>
            </div>
          </div>

          <div class="looking-for">
            <h3>Actualmente estoy buscando</h3>
            <p>{{ about.currentlyLooking }}</p>
          </div>

          <div class="cta">
            <a href="#contact" class="cta-button">¿Hablamos? →</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: 7rem 1.5rem 9rem;
  background: linear-gradient(135deg, #f9fafb 0%, #e5e7eb 100%);
}

@media (prefers-color-scheme: dark) {
  .about-section {
    background: linear-gradient(135deg, #111827 0%, #1f2937 100%);
  }
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 4rem;
}

@media (min-width: 768px) {
  .about-grid {
    grid-template-columns: 320px 1fr;
  }
}

.about-photo-column {
  text-align: center;
}

.photo-wrapper {
  position: relative;
  width: 220px;
  height: 220px;
  margin: 0 auto 1.5rem;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 15px 40px rgba(0,0,0,0.15);
}

@media (prefers-color-scheme: dark) {
  .photo-wrapper {
    box-shadow: 0 15px 40px rgba(0,0,0,0.6);
  }
}

.profile-photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.quick-info .name {
  font-size: 2.2rem;
  font-weight: 700;
  margin-bottom: 0.4rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .quick-info .name {
    color: #f3f4f6;
  }
}

.quick-info .role {
  font-size: 1.2rem;
  color: #4b5563;
  margin-bottom: 0.6rem;
}

@media (prefers-color-scheme: dark) {
  .quick-info .role {
    color: #9ca3af;
  }
}

.quick-info .location {
  font-size: 1rem;
  color: #6b7280;
}

@media (prefers-color-scheme: dark) {
  .quick-info .location {
    color: #9ca3af;
  }
}

.headline {
  font-size: 2.4rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 1.8rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .headline {
    color: #f3f4f6;
  }
}

.bio {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #374151;
  margin-bottom: 2.5rem;
}

@media (prefers-color-scheme: dark) {
  .bio {
    color: #d1d5db;
  }
}

.highlights {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.2rem;
  margin-bottom: 3rem;
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  background: rgba(99, 102, 241, 0.08);
  padding: 1rem 1.3rem;
  border-radius: 12px;
  font-size: 1rem;
  color: #374151;
}

@media (prefers-color-scheme: dark) {
  .highlight-item {
    background: rgba(99, 102, 241, 0.15);
    color: #d1d5db;
  }
}

.highlight-icon {
  font-size: 1.4rem;
}

.looking-for {
  margin-bottom: 2.5rem;
}

.looking-for h3 {
  font-size: 1.4rem;
  margin-bottom: 0.8rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .looking-for h3 {
    color: #f3f4f6;
  }
}

.looking-for p {
  font-size: 1.1rem;
  color: #4b5563;
}

@media (prefers-color-scheme: dark) {
  .looking-for p {
    color: #9ca3af;
  }
}

.cta-button {
  display: inline-block;
  padding: 1rem 2rem;
  background: #6366f1;
  color: white;
  font-weight: 600;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.25s;
}

.cta-button:hover {
  background: #4f46e5;
  transform: translateY(-2px);
}
</style>