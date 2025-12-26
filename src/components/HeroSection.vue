<template>
  <section class="hero">
    <div class="hero-content">
      <div class="profile-image-container">
        <img src="/profile_pic.jpeg" alt="Edwin Salcedo" class="profile-image" />
      </div>
      <h1>{{ data.name }}</h1>
      <p class="subtitle">{{ data.title }}</p>
      <p class="description">{{ data.description }}</p>
      <a
        href="/Edwin_Salcedo_Resume.pdf"
        target="_blank"
        rel="noopener noreferrer"
        class="resume-button"
      >
        My Resume
      </a>
    </div>
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

.hero-content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.profile-image-container {
  position: absolute;
  top: -240px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 0;
  animation: fadeIn 1s ease-out;
}

.profile-image {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  object-fit: cover;
  opacity: 0.9;
  transition: all 0.3s ease;
}

.hero-content h1 {
  position: relative;
  z-index: 1;
}

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
  position: relative;
  z-index: 1;
}

.resume-button:hover {
  background: var(--accent-hover);
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 113, 227, 0.3);
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 0.9;
  }
}

@media (max-width: 768px) {
  .profile-image {
    width: 200px;
    height: 200px;
  }

  .profile-image-container {
    top: -60px;
  }
}
</style>