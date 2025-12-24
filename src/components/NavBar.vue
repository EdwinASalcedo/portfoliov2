<template>
  <nav>
    <div class="nav-content">
      <ul class="nav-links">
        <li v-for="link in links" :key="link.name">
          <a :href="link.href">{{ link.name }}</a>
        </li>
      </ul>
      <div class="nav-actions">
        <div class="social-links">
          <a href="https://github.com/EdwinASalcedo" target="_blank" rel="noopener noreferrer" aria-label="GitHub">
            <img :src="githubIcon" alt="GitHub" width="20" height="20" />
          </a>
          <a href="https://www.linkedin.com/in/edwin-a-salcedo/" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn">
            <img :src="linkedinIcon" alt="LinkedIn" width="20" height="20" />
          </a>
          <a href="https://x.com/EdSauce_edo" target="_blank" rel="noopener noreferrer" aria-label="X (Twitter)">
            <img :src="xIcon" alt="X" width="20" height="20" />
          </a>
        </div>
        <button
          class="theme-toggle"
          @click="$emit('toggle-theme')"
          :aria-label="theme === 'light' ? 'Switch to dark mode' : 'Switch to light mode'"
        >
          {{ theme === 'light' ? '🌙' : '☀️' }}
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
import githubIcon from '@/assets/icons/github.svg'
import linkedinIcon from '@/assets/icons/linkedin.svg'
import xIcon from '@/assets/icons/x.svg'

export default {
  name: 'NavBar',
  props: {
    links: {
      type: Array,
      required: true
    },
    theme: {
      type: String,
      required: true
    }
  },
  emits: ['toggle-theme'],
  data() {
    return {
      githubIcon,
      linkedinIcon,
      xIcon
    }
  }
}
</script>

<style scoped>
nav {
  position: fixed;
  top: 0;
  width: 100%;
  background: var(--nav-blur);
  backdrop-filter: saturate(180%) blur(20px);
  -webkit-backdrop-filter: saturate(180%) blur(20px);
  border-bottom: 1px solid var(--border);
  z-index: 1000;
  transition: all 0.3s ease;
}

.nav-content {
  max-width: 980px;
  margin: 0 auto;
  padding: 0 22px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-links {
  display: flex;
  gap: 32px;
  list-style: none;
}

.nav-links a {
  color: var(--text-primary);
  text-decoration: none;
  font-size: 12px;
  font-weight: 400;
  opacity: 0.8;
  transition: opacity 0.3s ease;
  letter-spacing: -0.01em;
}

.nav-links a:hover {
  opacity: 1;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 16px;
}

.social-links {
  display: flex;
  align-items: center;
  gap: 16px;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0.8;
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.social-links a:hover {
  opacity: 1;
  transform: translateY(-2px);
}

.social-links img {
  filter: var(--icon-filter);
  transition: filter 0.3s ease;
}

.theme-toggle {
  background: none;
  border: none;
  color: var(--text-primary);
  cursor: pointer;
  font-size: 20px;
  opacity: 0.8;
  transition: opacity 0.3s ease, transform 0.3s ease;
  padding: 4px;
}

.theme-toggle:hover {
  opacity: 1;
  transform: scale(1.1);
}

@media (max-width: 768px) {
  .nav-links {
    gap: 16px;
  }
}
</style>