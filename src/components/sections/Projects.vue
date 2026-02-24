<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    title: 'E-commerce de ropa sostenible',
    description: 'Tienda online con carrito, filtros por categoría, autenticación y pasarela de pago (modo test).',
    technologies: ['Vue 3', 'Pinia', 'Firebase', 'Stripe'],
    image: 'https://images.unsplash.com/photo-1556740714-a8395b3a74dd?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
    link: 'https://github.com/...',
    demo: 'https://...',
    year: 2025,
    featured: false
  },
  {
    title: 'Dashboard de criptomonedas',
    description: 'Panel en tiempo real con precios, gráficos interactivos y alertas personalizadas.',
    technologies: ['Vue 3', 'Chart.js', 'Pinia', 'CoinGecko API'],
    image: 'https://images.unsplash.com/photo-1621504450181-5b0284445e93?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
    link: 'https://github.com/...',
    demo: 'https://...',
    featured: true
  },
  // ← agrega aquí tus proyectos reales
])
</script>

<template>
  <section id="projects" class="projects-section">
    <h2 class="section-title">Proyectos</h2>
    <p class="section-subtitle">
      Algunos de los trabajos de los que más orgulloso me siento
    </p>

    <div class="projects-grid">
      <article v-for="project in projects" :key="project.title" class="project-card">
        <div class="project-image-container">
          <img
            :src="project.image"
            :alt="project.title"
            class="project-image"
            loading="lazy"
          />
          <span v-if="project.featured" class="featured-badge">Destacado</span>
        </div>

        <div class="project-content">
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>

          <div class="tech-tags">
            <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>

          <div class="project-links">
            <a
              v-if="project.demo"
              :href="project.demo"
              target="_blank"
              rel="noopener noreferrer"
              class="link-demo"
            >
              Ver demo →
            </a>
            <a
              v-if="project.link"
              :href="project.link"
              target="_blank"
              rel="noopener noreferrer"
              class="link-github"
            >
              GitHub →
            </a>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 5rem 1.5rem;
  background: #f8f9fa;
}

@media (prefers-color-scheme: dark) {
  .projects-section {
    background: #121212;
    color: #e0e0e0;
  }
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 0.75rem;
  color: #1a1a1a;
}

@media (prefers-color-scheme: dark) {
  .section-title {
    color: #ffffff;
  }
}

.section-subtitle {
  text-align: center;
  color: #666;
  margin-bottom: 3.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  font-size: 1.1rem;
}

@media (prefers-color-scheme: dark) {
  .section-subtitle {
    color: #bbbbbb;
  }
}

.projects-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

@media (min-width: 640px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.project-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
}

@media (prefers-color-scheme: dark) {
  .project-card {
    background: #1e1e1e;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
  }
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.12);
}

@media (prefers-color-scheme: dark) {
  .project-card:hover {
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.6);
  }
}

.project-image-container {
  position: relative;
  aspect-ratio: 16 / 9;
  overflow: hidden;
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.project-card:hover .project-image {
  transform: scale(1.08);
}

.featured-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  background: #f59e0b;
  color: white;
  font-size: 0.75rem;
  font-weight: bold;
  padding: 0.35rem 0.75rem;
  border-radius: 9999px;
}

.project-content {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.project-title {
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .project-title {
    color: #f3f4f6;
  }
}

.project-description {
  color: #4b5563;
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 1.25rem;
  flex-grow: 1;
}

@media (prefers-color-scheme: dark) {
  .project-description {
    color: #d1d5db;
  }
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.25rem;
}

.tech-tag {
  background: #e5e7eb;
  color: #374151;
  font-size: 0.8rem;
  padding: 0.35rem 0.85rem;
  border-radius: 9999px;
}

@media (prefers-color-scheme: dark) {
  .tech-tag {
    background: #374151;
    color: #e5e7eb;
  }
}

.project-links {
  display: flex;
  gap: 1.5rem;
  margin-top: auto;
}

.link-demo {
  color: #2563eb;
  font-weight: 500;
  text-decoration: none;
  font-size: 0.95rem;
}

.link-demo:hover {
  text-decoration: underline;
}

@media (prefers-color-scheme: dark) {
  .link-demo {
    color: #60a5fa;
  }
}

.link-github {
  color: #4b5563;
  font-size: 0.95rem;
  text-decoration: none;
}

.link-github:hover {
  color: #111827;
  text-decoration: underline;
}

@media (prefers-color-scheme: dark) {
  .link-github {
    color: #9ca3af;
  }
  .link-github:hover {
    color: #f3f4f6;
  }
}
</style>