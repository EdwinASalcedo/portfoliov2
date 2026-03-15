<template>
  <section class="w-full pt-11 pb-20 px-5.5 min-h-[80vh] flex items-center bg-white dark:bg-black max-md:pb-15 max-md:px-4">
    <div class="max-w-245 mx-auto w-full flex items-center gap-16 max-md:flex-col max-md:gap-10 max-md:pt-12 max-md:text-center">

      <!-- Left: Profile image -->
      <div class="shrink-0">
        <img
          src="/profile_pic.jpeg"
          alt="Edwin Salcedo"
          class="w-72 h-72 rounded-full object-cover max-md:w-44 max-md:h-44"
        />
      </div>

      <!-- Right: Text + CTA + Socials -->
      <div class="flex flex-col items-start max-md:items-center">
        <h1 class="text-[72px] font-semibold tracking-[-0.015em] leading-[1.05] mb-2 text-neutral-900 dark:text-white max-md:text-[48px]">{{ data.name }}</h1>
        <p class="text-[26px] font-normal text-neutral-900 dark:text-neutral-100 mb-5 tracking-[-0.01em] max-md:text-[21px]">{{ data.title }}</p>
        <p class="max-w-130 text-[19px] leading-normal text-neutral-900 dark:text-neutral-100 font-normal tracking-[-0.01em] mb-8 max-md:text-[17px] max-md:max-w-full">{{ data.description }}</p>

        <!-- Resume button + social icons -->
        <div class="flex items-center gap-5 max-md:flex-col max-md:gap-4">
          <a
            href="/Edwin_Salcedo_Resume.pdf"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-block px-8 py-3 bg-accent text-white no-underline rounded-full text-[17px] font-medium tracking-[-0.01em] hover:bg-accent-hover transition-colors"
          >My Resume</a>

          <div class="flex items-center gap-4">
            <a href="https://github.com/EdwinASalcedo" target="_blank" rel="noopener noreferrer" aria-label="GitHub"
              class="flex items-center opacity-60 hover:opacity-100 transition-opacity">
              <img :src="githubIcon" alt="GitHub" width="22" height="22" class="dark:invert dark:brightness-125" />
            </a>
            <a href="https://www.linkedin.com/in/edwin-a-salcedo/" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn"
              class="flex items-center opacity-60 hover:opacity-100 transition-opacity">
              <img :src="linkedinIcon" alt="LinkedIn" width="22" height="22" class="dark:invert dark:brightness-125" />
            </a>
            <a href="https://x.com/EdSauce_edo" target="_blank" rel="noopener noreferrer" aria-label="X"
              class="flex items-center opacity-60 hover:opacity-100 transition-opacity">
              <img :src="xIcon" alt="X" width="22" height="22" class="dark:invert dark:brightness-125" />
            </a>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
import githubIcon from '@/assets/icons/github.svg'
import linkedinIcon from '@/assets/icons/linkedin.svg'
import xIcon from '@/assets/icons/x.svg'

export default {
  name: 'HeroSection',
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      githubIcon,
      linkedinIcon,
      xIcon,
    }
  }
}
</script>

<style scoped>
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.97); }
  to   { opacity: 1; transform: scale(1); }
}
.profile-img-animated {
  animation: fadeIn 0.8s ease-out;
}
</style>
