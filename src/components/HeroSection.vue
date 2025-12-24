<template>
  <section class="hero">
    <h1>{{ data.name }}</h1>
    <p class="subtitle">{{ data.title }}</p>
    <p class="description">{{ data.description }}</p>
    <a
      href="/Edwin_Salcedo_Resume.pdf"
      download="Edwin_Salcedo_Resume.pdf"
      class="resume-button"
    >
      My Resume
    </a>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
/* Hero styles are in main.css for global access */

.resume-button {
  display: inline-block;
  margin-top: 32px;
  padding: 12px 32px;
  background: var(--accent);
  color: white;
  text-decoration: none;
  border-radius: 980px;
  font-size: 17px;
  font-weight: 500;
  transition: all 0.3s ease;
  letter-spacing: -0.01em;
  animation: fadeInUp 0.8s ease-out 0.3s both;
}

.resume-button:hover {
  background: var(--accent-hover);
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 113, 227, 0.3);
}
</style>