<template>
  <div id="app">
    <NavBar
      :links="navLinks"
      :theme="theme"
      @toggle-theme="toggleTheme"
    />
    <RouterView />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    NavBar
  },
  data() {
    return {
      theme: localStorage.getItem('theme') || 'light',
      navLinks: [
        { name: 'About', href: '/#about' },
        { name: 'Apps', href: '/#apps' },
        { name: 'Experience', href: '/#experience' },
        { name: 'Projects', href: '/#projects' },
        { name: 'Education', href: '/#education' },
        { name: "WOM", href: '/wom' },
      ],
    }
  },
  mounted() {
    this.applyTheme()
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light'
      localStorage.setItem('theme', this.theme)
      this.applyTheme()
    },
    applyTheme() {
      document.documentElement.setAttribute('data-theme', this.theme)
    }
  }
}
</script>
