<template>
  <div id="app">
    <NavBar 
      :links="navLinks"
      :theme="theme"
      @toggle-theme="toggleTheme"
    />

    <HeroSection :data="hero" id="about" />

    <section id="apps" class="section section-full" style="background: var(--bg-secondary);">
      <div class="section-content">
      <div class="section-header">
        <h2 class="section-title">Featured Apps</h2>
        <p class="section-subtitle">Available on the App Store</p>
      </div>
      <FeaturedApps :apps="featuredApps" />
    </div>
    </section>

    <section id="experience" class="section">
      <div class="section-content">
        <div class="section-header">
          <h2 class="section-title">Experience</h2>
          <p class="section-subtitle"></p>
        </div>
        <TimelineComponent :items="experiences" />
      </div>
    </section>

    <section id="projects" class="section section-full" style="background: var(--bg-secondary);">
      <div class="section-content">
      <div class="section-header">
        <h2 class="section-title">Projects</h2>
        <p class="section-subtitle"></p>
      </div>
      <CardGrid :items="projects" cardBg="primary"/>
      </div>
    </section>

    <section id="education" class="section">
      <div class="section-content">
        <div class="section-header">
          <h2 class="section-title">Education</h2>
          <p class="section-subtitle">GO GATORS!</p>
        </div>
        <CardGrid :items="education" cardBg="secondary"/>
      </div>
    </section>

  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import TimelineComponent from './components/TimelineComponent.vue'
import CardGrid from './components/CardGrid.vue'
import FeaturedApps from './components/FeaturedApps.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    HeroSection,
    TimelineComponent,
    CardGrid,
    FeaturedApps
  },
  data() {
    return {
      theme: localStorage.getItem('theme') || 'light',
      navLinks: [
        { name: 'About', href: '#about' },
        { name: 'Apps', href: '#apps' },
        { name: 'Experience', href: '#experience' },
        { name: 'Projects', href: '#projects' },
        { name: 'Education', href: '#education' },        
      ],
      hero: {
        name: 'Edwin Salcedo',
        title: 'iOS Software Engineer',
        description: 'Crafting intuitive and functional experiences that make a difference. Passionate about app architecture, user experience, and building products people love. Now learning graphics programming using the Metal framework by Apple'
      },
      experiences: [
        {
          title: 'iOS Software Engineer',
          company: 'Lift Notes (personal project)',
          date: 'September 2025 - Present',
          description: '• Designed, built, and published LiftLog, a weightlifting tracker app using SwiftUI and SwiftData \n• Released on the App Store, achieving 70+ downloads and ongoing user growth \n• Collected and integrated user feedback, releasing bug fixes and updates to enhance UX \n• Implemented data persistence and smooth, responsive animations using native SwiftUI \n• Utilized XCTest and XCUITest for unit testing'
        },
        {
          title: 'GIS Data Scientist Intern',
          company: 'UF IFAS Ecosystem Services A.I Lab',
          date: 'May 2024 - September 2024',
          description: '• Built python scripts using Google Earth Engine, OpenStreetMap, GeoPandas, and geemap to extract, filter, and visualize Florida geospatial data for AI model training\n• Documented the data pipeline and script usage, writing clear setup and usage instructions for future lab members to reproduce and build upon the work\n• Presented findings through a technical slideshow, contributing to the professor’s conference presentation, which spurred external interest and new research partnerships\n• Researched data collection methodologies in the early project phase, analyzing academic literature to design an effective approach to satellite imagery labeling for AI modeling'
        },
      ],
      projects: [
        {
          title: 'LiftNotes',
          subtitle: 'iOS App',
          date: '2025',
          description: 'A comprehensive design system with 100+ components, documentation, and guidelines for building consistent user interfaces.',
          tags: ['SwiftUI', 'SwiftData', 'Swift',]
        },
        {
          title: 'A.I Chat App',
          subtitle: 'iOS App',
          date: '2025',
          description: 'Built a modern e-commerce platform with advanced filtering, real-time inventory, and seamless checkout experience.',
          tags: ['SwiftUI', 'Firebase Database', 'OpenAI API', 'RevenueCat', 'Firebase Analytics', 'Firebase Storage',]
        },
        {
          title: 'Task Management App',
          subtitle: 'Mobile & Web',
          date: '2021',
          description: 'Collaborative task management tool with real-time updates, team workspaces, and intelligent prioritization.',
          tags: ['React', 'Firebase', 'Material-UI']
        }
      ],
      education: [
        {
          title: 'Computer Science, B.S.',
          subtitle: 'University of Florida',
          date: '2021 - 2025',
          description: 'Built my foundation of computer science theoritically and practically with a focus on software engineering'
        },
        {
          title: 'Minor in Digital Arts & Sciences',
          subtitle: 'University of Florida',
          date: '2024 - 2025',
          description: 'Focused on game developement using Unity and collaborating with fellow artists and programmers'
        }
      ],
      featuredApps: [
        {
          name: 'LiftNotes',
          description: 'Track your gym progress and make gains!',
          icon: '/app_icons/LiftNotes_logo.png',
          link: 'https://apps.apple.com/us/app/lift-notes-gym-tracker/id6753324391'
        },
        {
          name: 'Taste & Tell (W.I.P)',
          description: 'Discover and review your favorite food spots!',
          icon: '/app_icons/xcode.png',
          link: ''
        },
        {
          name: 'MoodJo (W.I.P)',
          description: 'Log your mood along with a journal entry.',
          icon: '/app_icons/xcode.png',
          link: ''
        },
      ]
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