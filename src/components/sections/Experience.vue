<script setup>
import { ref } from 'vue'

const experiences = ref([
  {
    date: 'Marzo 2024 – Presente',
    role: 'Desarrollador Frontend',
    company: 'TechNova Solutions',
    location: 'Managua, Nicaragua (Remoto)',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
    achievements: [
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
      'Duis aute irure dolor in reprehenderit in voluptate velit esse.',
      'Excepteur sint occaecat cupidatat non proident, sunt in culpa.',
      'Sed ut perspiciatis unde omnis iste natus error sit voluptatem.',
      'Nemo enim ipsam voluptatem quia voluptas sit aspernatur.'
    ]
  },
  {
    date: 'Enero 2022 – Febrero 2024',
    role: 'Desarrollador Full Stack',
    company: 'CreativeSoft Nicaragua',
    location: 'Managua, Nicaragua',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.',
    achievements: [
      'At vero eos et accusamus et iusto odio dignissimos ducimus.',
      'Totam rem aperiam, eaque ipsa quae ab illo inventore veritatis.',
      'Beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem.',
      'Quia voluptas sit aspernatur aut odit aut fugit, sed quia.',
      'Consequuntur magni dolores eos qui ratione voluptatem sequi.'
    ]
  },
  {
    date: 'Junio 2020 – Diciembre 2021',
    role: 'Desarrollador Junior Vue.js',
    company: 'StartUp Digital NI',
    location: 'Managua, Nicaragua',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
    achievements: [
      'Neque porro quisquam est, qui dolorem ipsum quia dolor sit.',
      'Amet, consectetur, adipisci velit, sed quia non numquam.',
      'Eius modi tempora incidunt ut labore et dolore magnam.',
      'Aliquam quaerat voluptatem. Ut enim ad minima veniam.',
      'Quis nostrum exercitationem ullam corporis suscipit laboriosam.'
    ]
  },
  {
    date: 'Marzo 2019 – Mayo 2020',
    role: 'Practicante Desarrollo Web',
    company: 'Agencia Web 502',
    location: 'Remoto',
    description: 'Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
    achievements: [
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
      'Sed do eiusmod tempor incididunt ut labore et dolore.',
      'Magna aliqua. Ut enim ad minim veniam, quis nostrud.',
      'Exercitation ullamco laboris nisi ut aliquip ex ea.',
      'Commodo consequat. Duis aute irure dolor in reprehenderit.'
    ]
  },
  // Puedes agregar más o quitar las que no necesites
])
</script>

<template>
  <section id="experience" class="experience-section">
    <h2 class="section-title">Experiencia</h2>
    <p class="section-subtitle">Mi recorrido profesional hasta la fecha</p>

    <div class="timeline-container">
      <div class="timeline-line"></div>

      <div class="timeline-items">
        <article
          v-for="(exp, index) in experiences"
          :key="index"
          class="timeline-item"
          :class="{ 'left-side': index % 2 === 0, 'right-side': index % 2 !== 0 }"
        >
          <div class="timeline-dot"></div>
          <div class="timeline-card">
            <div class="timeline-date">{{ exp.date }}</div>
            <h3 class="timeline-role">{{ exp.role }}</h3>
            <div class="timeline-company">
              {{ exp.company }} • {{ exp.location }}
            </div>
            <p class="timeline-description">{{ exp.description }}</p>

            <ul class="achievements-list">
              <li v-for="(point, i) in exp.achievements" :key="i">
                {{ point }}
              </li>
            </ul>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 5rem 1.5rem;
  background: #f8f9fa;
}

@media (prefers-color-scheme: dark) {
  .experience-section {
    background: #0f0f0f;
  }
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: #111;
}

@media (prefers-color-scheme: dark) {
  .section-title {
    color: #eee;
  }
}

.section-subtitle {
  text-align: center;
  color: #555;
  margin-bottom: 4rem;
  font-size: 1.15rem;
}

@media (prefers-color-scheme: dark) {
  .section-subtitle {
    color: #aaa;
  }
}

/* ─── Timeline ──────────────────────────────────────── */
.timeline-container {
  position: relative;
  max-width: 1100px;
  margin: 0 auto;
}

.timeline-line {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 4px;
  background: #6366f1;
  transform: translateX(-50%);
  border-radius: 2px;
}

.timeline-items {
  position: relative;
  padding: 1rem 0;
}

.timeline-item {
  position: relative;
  margin: 3rem 0;
  width: 50%;
  padding: 0 2.5rem;
}

.left-side {
  left: 0;
  text-align: right;
}

.right-side {
  left: 50%;
  text-align: left;
}

.timeline-dot {
  position: absolute;
  top: 28px;
  width: 18px;
  height: 18px;
  background: #6366f1;
  border: 4px solid #fff;
  border-radius: 50%;
  box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.2);
  z-index: 10;
}

.left-side .timeline-dot {
  right: -9px;
}

.right-side .timeline-dot {
  left: -9px;
}

@media (prefers-color-scheme: dark) {
  .timeline-dot {
    border-color: #1a1a1a;
  }
}

.timeline-card {
  background: white;
  padding: 1.6rem 1.8rem;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.08);
  position: relative;
  transition: transform 0.25s ease;
}

.timeline-card:hover {
  transform: translateY(-6px);
}

@media (prefers-color-scheme: dark) {
  .timeline-card {
    background: #1e1e1e;
    box-shadow: 0 6px 24px rgba(0,0,0,0.5);
  }
}

.timeline-date {
  font-size: 0.95rem;
  color: #666;
  font-weight: 500;
  margin-bottom: 0.4rem;
}

@media (prefers-color-scheme: dark) {
  .timeline-date {
    color: #bbb;
  }
}

.timeline-role {
  font-size: 1.35rem;
  font-weight: 600;
  margin-bottom: 0.3rem;
  color: #111;
}

@media (prefers-color-scheme: dark) {
  .timeline-role {
    color: #fff;
  }
}

.timeline-company {
  font-size: 1rem;
  color: #555;
  margin-bottom: 1rem;
}

@media (prefers-color-scheme: dark) {
  .timeline-company {
    color: #ccc;
  }
}

.timeline-description {
  font-size: 0.97rem;
  line-height: 1.6;
  color: #444;
  margin-bottom: 1.2rem;
}

@media (prefers-color-scheme: dark) {
  .timeline-description {
    color: #ddd;
  }
}

.achievements-list {
  list-style: none;
  padding: 0;
  margin: 0;
  font-size: 0.95rem;
  color: #555;
}

@media (prefers-color-scheme: dark) {
  .achievements-list {
    color: #ccc;
  }
}

.achievements-list li {
  position: relative;
  padding-left: 1.6rem;
  margin-bottom: 0.5rem;
}

.achievements-list li::before {
  content: "•";
  position: absolute;
  left: 0;
  color: #6366f1;
  font-size: 1.4rem;
  line-height: 1;
}

/* Mobile: todo a la izquierda */
@media (max-width: 768px) {
  .timeline-line {
    left: 28px;
  }

  .timeline-item {
    width: 100%;
    left: 0 !important;
    padding: 0 0 0 4.5rem;
    text-align: left !important;
  }

  .timeline-dot {
    left: 10px !important;
  }

  .timeline-card {
    margin-left: 0;
  }
}
</style>