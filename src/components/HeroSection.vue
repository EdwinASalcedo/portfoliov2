<template>
  <section class="pt-90 pb-20 px-5.5 text-center min-h-[70vh] flex flex-col justify-center items-center bg-white dark:bg-black scroll-mt-15 max-md:pt-40 max-md:pb-15 max-md:px-4 max-md:min-h-[60vh]">
    <div class="relative flex flex-col items-center">
      <div class="absolute -top-60 left-1/2 -translate-x-1/2 z-0 max-md:hidden">
        <img src="/profile_pic.jpeg" alt="Edwin Salcedo" class="profile-img-animated w-75 h-75 rounded-full object-cover opacity-90" />
      </div>
      <h1 class="relative z-1 text-[80px] font-semibold tracking-[-0.015em] leading-[1.05] mb-3 gradient-text max-md:text-5xl">{{ data.name }}</h1>
      <p class="text-[28px] font-normal text-neutral-500 dark:text-neutral-400 mb-8 tracking-[-0.01em] max-md:text-[21px]">{{ data.title }}</p>
      <p class="max-w-150 text-[21px] leading-[1.4] text-neutral-600 dark:text-neutral-500 font-normal tracking-[-0.01em] max-md:text-[17px] max-md:max-w-full">{{ data.description }}</p>
      <a
        href="/Edwin_Salcedo_Resume.pdf"
        target="_blank"
        rel="noopener noreferrer"
        class="relative z-1 inline-block mt-8 px-8 py-3 bg-accent text-white no-underline rounded-full text-[17px] font-medium tracking-[-0.01em] hover:bg-[#0051d5]"
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
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 0.9; }
}
.profile-img-animated {
  animation: fadeIn 1s ease-out;
}
</style>
