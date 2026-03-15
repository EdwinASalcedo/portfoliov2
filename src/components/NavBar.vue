<template>
  <!-- Desktop / Mobile bar -->
  <nav class="fixed top-0 w-full bg-white/80 dark:bg-black/80 backdrop-saturate-180 backdrop-blur-xl border-b border-neutral-200 dark:border-white/10 z-1000">
    <div class="max-w-245 mx-auto px-5.5 max-md:px-4 h-11 flex items-center justify-between">

      <!-- Desktop: nav links left -->
      <ul class="flex gap-8 list-none max-md:hidden">
        <li v-for="link in links" :key="link.name">
          <RouterLink
            v-if="link.href.startsWith('/')"
            :to="link.href"
            class="text-neutral-900 dark:text-neutral-100 no-underline text-[12px] font-normal opacity-80 hover:opacity-100 tracking-[-0.01em]"
          >{{ link.name }}</RouterLink>
          <a
            v-else
            :href="link.href"
            class="text-neutral-900 dark:text-neutral-100 no-underline text-[12px] font-normal opacity-80 hover:opacity-100 tracking-[-0.01em]"
          >{{ link.name }}</a>
        </li>
      </ul>

      <!-- Mobile: name left -->
      <span class="hidden max-md:block text-[14px] font-semibold text-neutral-900 dark:text-neutral-100 tracking-[-0.01em]">
        Edwin Salcedo
      </span>

      <!-- Right: social icons (desktop) + theme toggle + hamburger (mobile) -->
      <div class="flex items-center gap-4">
        <!-- Theme toggle -->
        <button
          class="bg-transparent border-none text-neutral-900 dark:text-neutral-100 cursor-pointer text-xl opacity-80 hover:opacity-100 p-1"
          @click="$emit('toggle-theme')"
          :aria-label="theme === 'light' ? 'Switch to dark mode' : 'Switch to light mode'"
        >
          {{ theme === 'light' ? '🌙' : '☀️' }}
        </button>

        <!-- Hamburger / X: mobile only -->
        <button
          class="hidden max-md:flex items-center justify-center bg-transparent border-none cursor-pointer p-1 text-neutral-900 dark:text-neutral-100 opacity-80 hover:opacity-100"
          @click="menuOpen = !menuOpen"
          :aria-label="menuOpen ? 'Close menu' : 'Open menu'"
        >
          <template v-if="menuOpen">
            <span class="text-[20px] leading-none">✕</span>
          </template>
          <template v-else>
            <span class="flex flex-col gap-1.25">
              <span class="block w-3.75 h-0.5 bg-neutral-900 dark:bg-neutral-100 rounded-full"></span>
              <span class="block w-3.75 h-0.5 bg-neutral-900 dark:bg-neutral-100 rounded-full"></span>
            </span>
          </template>
        </button>

      </div>
    </div>
  </nav>

  <!-- Mobile menu overlay: starts below the navbar -->
  <Teleport to="body">
    <Transition name="menu-slide">
      <div
        v-if="menuOpen"
        class="fixed top-11 inset-x-0 bottom-0 z-999 bg-white dark:bg-black flex flex-col md:hidden"
      >
        <!-- Nav links: vertically centered -->
        <div class="flex-1 flex flex-col items-center justify-center gap-8">
          <template v-for="link in links" :key="link.name">
            <RouterLink
              v-if="link.href.startsWith('/')"
              :to="link.href"
              class="text-[32px] font-semibold text-neutral-900 dark:text-neutral-100 no-underline opacity-90 hover:opacity-100 tracking-[-0.02em]"
              @click="menuOpen = false"
            >{{ link.name }}</RouterLink>
            <a
              v-else
              :href="link.href"
              class="text-[32px] font-semibold text-neutral-900 dark:text-neutral-100 no-underline opacity-90 hover:opacity-100 tracking-[-0.02em]"
              @click="menuOpen = false"
            >{{ link.name }}</a>
          </template>
        </div>

        <!-- Social icons at bottom -->
        <div class="flex items-center justify-center gap-8 pb-12 shrink-0">
          <a href="https://github.com/EdwinASalcedo" target="_blank" rel="noopener noreferrer" aria-label="GitHub"
            class="flex items-center opacity-80 hover:opacity-100">
            <img :src="githubIcon" alt="GitHub" width="28" height="28" class="dark:invert dark:brightness-125" />
          </a>
          <a href="https://www.linkedin.com/in/edwin-a-salcedo/" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn"
            class="flex items-center opacity-80 hover:opacity-100">
            <img :src="linkedinIcon" alt="LinkedIn" width="28" height="28" class="dark:invert dark:brightness-125" />
          </a>
          <a href="https://x.com/EdSauce_edo" target="_blank" rel="noopener noreferrer" aria-label="X (Twitter)"
            class="flex items-center opacity-80 hover:opacity-100">
            <img :src="xIcon" alt="X" width="28" height="28" class="dark:invert dark:brightness-125" />
          </a>
        </div>
      </div>
    </Transition>
  </Teleport>
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
      xIcon,
      menuOpen: false
    }
  },
  watch: {
    menuOpen(val) {
      document.body.style.overflow = val ? 'hidden' : ''
    }
  }
}
</script>

<style scoped>
.menu-slide-enter-active,
.menu-slide-leave-active {
  transition: opacity 0.25s ease, transform 0.25s ease;
}

.menu-slide-enter-from,
.menu-slide-leave-to {
  opacity: 0;
  transform: translateY(-12px);
}

.menu-slide-enter-to,
.menu-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
