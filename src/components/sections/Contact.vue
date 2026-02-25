<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const errors = ref({
  name: '',
  email: '',
  message: ''
})

const isSubmitting = ref(false)
const submitSuccess = ref(false)
const submitError = ref(false)

const validateForm = () => {
  let isValid = true
  errors.value = { name: '', email: '', message: '' }

  if (!form.value.name.trim()) {
    errors.value.name = 'El nombre es requerido'
    isValid = false
  }

  if (!form.value.email.trim()) {
    errors.value.email = 'El email es requerido'
    isValid = false
  } else if (!/\S+@\S+\.\S+/.test(form.value.email)) {
    errors.value.email = 'Email inválido'
    isValid = false
  }

  if (!form.value.message.trim()) {
    errors.value.message = 'El mensaje no puede estar vacío'
    isValid = false
  }

  return isValid
}

const handleSubmit = async () => {
  if (!validateForm()) return

  isSubmitting.value = true
  submitSuccess.value = false
  submitError.value = false

  // Aquí iría la lógica real de envío (Formspree, EmailJS, backend propio, etc.)
  // Ejemplo simulado:
  try {
    // await sendEmail(form.value)
    await new Promise(resolve => setTimeout(resolve, 1200)) // simulación
    submitSuccess.value = true
    form.value = { name: '', email: '', message: '' }
  } catch (err) {
    submitError.value = true
  } finally {
    isSubmitting.value = false
  }
}

// Opcional: enlaces reales tuyos
const socialLinks = [
  { name: 'GitHub', url: 'https://github.com/tu-usuario', icon: 'github' },
  { name: 'LinkedIn', url: 'https://linkedin.com/in/tu-perfil', icon: 'linkedin' },
  { name: 'Email', url: 'mailto:tuemail@ejemplo.com', icon: 'mail' },
  // Agrega más: Twitter/X, WhatsApp, etc.
]
</script>

<template>
  <section id="contact" class="contact-section">
    <div class="container">
      <h2 class="section-title">Contacto</h2>
      <p class="section-subtitle">
        ¿Quieres colaborar en un proyecto, charlar sobre Vue o simplemente saludar? ¡Estoy a un mensaje!
      </p>

      <div class="contact-content">
        <!-- Columna izquierda - Formulario -->
        <div class="contact-form-wrapper">
          <form @submit.prevent="handleSubmit" class="contact-form">
            <div class="form-group">
              <label for="name">Nombre</label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                placeholder="Tu nombre completo"
                :class="{ 'input-error': errors.name }"
              />
              <span v-if="errors.name" class="error-text">{{ errors.name }}</span>
            </div>

            <div class="form-group">
              <label for="email">Email</label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                placeholder="tu.email@ejemplo.com"
                :class="{ 'input-error': errors.email }"
              />
              <span v-if="errors.email" class="error-text">{{ errors.email }}</span>
            </div>

            <div class="form-group">
              <label for="message">Mensaje</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                placeholder="Cuéntame sobre tu idea o proyecto..."
                :class="{ 'input-error': errors.message }"
              ></textarea>
              <span v-if="errors.message" class="error-text">{{ errors.message }}</span>
            </div>

            <button
              type="submit"
              class="submit-btn"
              :disabled="isSubmitting"
            >
              {{ isSubmitting ? 'Enviando...' : 'Enviar mensaje' }}
            </button>

            <div v-if="submitSuccess" class="success-message">
              ¡Mensaje enviado! Te responderé lo antes posible 😊
            </div>
            <div v-if="submitError" class="error-message">
              Hubo un error al enviar. Inténtalo de nuevo o contáctame directamente por email.
            </div>
          </form>
        </div>

        <!-- Columna derecha - Info alternativa + redes -->
        <div class="contact-info">
          <h3 class="info-title">Otras formas de contactarme</h3>
          
          <div class="info-item">
            <span class="icon">✉️</span>
            <div>
              <strong>Email directo</strong>
              <a href="mailto:tuemail@ejemplo.com">tuemail@ejemplo.com</a>
            </div>
          </div>

          <div class="info-item">
            <span class="icon">📱</span>
            <div>
              <strong>WhatsApp / Teléfono</strong>
              <a href="https://wa.me/505tuNumero">+505 1234-5678</a>
            </div>
          </div>

          <div class="social-links">
            <a
              v-for="link in socialLinks"
              :key="link.name"
              :href="link.url"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
              :class="link.icon"
            >
              {{ link.name }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  padding: 6rem 1.5rem 8rem;
  background: #f9fafb;
}

@media (prefers-color-scheme: dark) {
  .contact-section {
    background: #111827;
  }
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

.section-title {
  text-align: center;
  font-size: 2.8rem;
  font-weight: 700;
  margin-bottom: 0.8rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .section-title {
    color: #f3f4f6;
  }
}

.section-subtitle {
  text-align: center;
  color: #4b5563;
  font-size: 1.15rem;
  margin-bottom: 4rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

@media (prefers-color-scheme: dark) {
  .section-subtitle {
    color: #9ca3af;
  }
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3.5rem;
}

@media (min-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr 1fr;
  }
}

.contact-form-wrapper {
  background: white;
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.08);
}

@media (prefers-color-scheme: dark) {
  .contact-form-wrapper {
    background: #1f2937;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  }
}

.form-group {
  margin-bottom: 1.8rem;
}

label {
  display: block;
  margin-bottom: 0.6rem;
  font-weight: 500;
  color: #374151;
}

@media (prefers-color-scheme: dark) {
  label {
    color: #d1d5db;
  }
}

input, textarea {
  width: 100%;
  padding: 0.9rem 1.1rem;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 1rem;
  background: white;
  transition: border-color 0.2s;
}

@media (prefers-color-scheme: dark) {
  input, textarea {
    background: #374151;
    border-color: #4b5563;
    color: #f3f4f6;
  }
}

input:focus, textarea:focus {
  outline: none;
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
}

.input-error {
  border-color: #ef4444 !important;
}

.error-text {
  color: #ef4444;
  font-size: 0.875rem;
  margin-top: 0.35rem;
  display: block;
}

.submit-btn {
  width: 100%;
  padding: 1rem;
  background: #6366f1;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

.submit-btn:hover:not(:disabled) {
  background: #4f46e5;
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.success-message {
  margin-top: 1.2rem;
  padding: 1rem;
  background: #d1fae5;
  color: #065f46;
  border-radius: 8px;
  text-align: center;
}

.error-message {
  margin-top: 1.2rem;
  padding: 1rem;
  background: #fee2e2;
  color: #991b1b;
  border-radius: 8px;
  text-align: center;
}

.contact-info {
  padding: 1rem;
}

.info-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1.8rem;
  color: #111827;
}

@media (prefers-color-scheme: dark) {
  .info-title {
    color: #f3f4f6;
  }
}

.info-item {
  display: flex;
  align-items: flex-start;
  margin-bottom: 1.8rem;
}

.icon {
  font-size: 1.6rem;
  margin-right: 1rem;
  color: #6366f1;
}

.info-item strong {
  display: block;
  margin-bottom: 0.3rem;
}

.info-item a {
  color: #2563eb;
  text-decoration: none;
}

.info-item a:hover {
  text-decoration: underline;
}

@media (prefers-color-scheme: dark) {
  .info-item a {
    color: #60a5fa;
  }
}

.social-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-top: 2rem;
}

.social-icon {
  display: inline-flex;
  align-items: center;
  padding: 0.6rem 1.2rem;
  background: #f3f4f6;
  border-radius: 9999px;
  text-decoration: none;
  font-size: 0.95rem;
  color: #374151;
  transition: all 0.2s;
}

.social-icon:hover {
  background: #e5e7eb;
  transform: translateY(-2px);
}

@media (prefers-color-scheme: dark) {
  .social-icon {
    background: #374151;
    color: #e5e7eb;
  }
  .social-icon:hover {
    background: #4b5563;
  }
}

/* Iconos de ejemplo (puedes usar SVG o librería como heroicons/vue) */
.github::before { content: "🐙 "; }
.linkedin::before { content: "💼 "; }
.mail::before   { content: "✉️ "; }
</style>