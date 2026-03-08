<template>
  <div>

    <!-- Hero: screenshot left, text right -->
    <section class="hero relative min-h-[50vh] flex items-center justify-center py-20 px-11 bg-white dark:bg-black overflow-hidden max-md:py-15 max-md:px-5.5">
      <img src="/app_icons/WOM_logo.png" alt="" aria-hidden="true" class="hero-logo-bg" />
      <div class="hero-inner relative z-1 grid grid-cols-2 items-center max-w-250 w-full max-md:grid-cols-1 max-md:gap-10 max-md:text-center">
        <div class="flex justify-center items-center">
          <div class="fan-container relative">
            <img src="/screenshots/IMG_4562.PNG" alt="App screenshot" class="fan-img fan-left" />
            <img src="/screenshots/IMG_4558.PNG" alt="App screenshot" class="fan-img fan-center" />
            <img src="/screenshots/IMG_4559.PNG" alt="App screenshot" class="fan-img fan-right" />
          </div>
        </div>
        <div class="flex flex-col items-start text-left max-md:items-center max-md:text-center">
          <h1 class="text-[clamp(32px,5vw,52px)] font-bold tracking-[-0.03em] text-neutral-900 dark:text-neutral-100 mb-2.5">Word O' Mouth</h1>
          <p class="text-[clamp(16px,2.5vw,22px)] font-medium text-neutral-500 dark:text-neutral-400 mb-4">Never have food FOMO again</p>
          <p class="text-[16px] leading-[1.65] text-neutral-500 dark:text-neutral-400 mb-8">
            Explore food recommendations from friends on the map, or leave reviews of your own.
            Discover your next favorite spot through people you trust.
            Enjoy the look of Apple Liquid Glass through iOS 26
          </p>
          <a
            href="https://testflight.apple.com/join/WVu7u7ED"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-block bg-neutral-900 text-white dark:bg-neutral-100 dark:text-black text-[15px] font-semibold py-3.5 px-8 rounded-full no-underline tracking-[-0.01em] hover:opacity-80"
          >
            Join the Beta on TestFlight
          </a>
          <p class="mt-3 text-[13px] text-neutral-500 dark:text-neutral-400">Requires iOS 26</p>
        </div>
      </div>
    </section>

    <!-- Features: 3 screenshots with captions below -->
    <section class="py-8 px-11 bg-neutral-100 dark:bg-neutral-900 max-md:py-15 max-md:px-5.5">
      <div class="max-w-250 mx-auto">
        <h2 class="text-[clamp(24px,4vw,36px)] font-bold tracking-[-0.02em] text-neutral-900 dark:text-neutral-100 text-center mb-12">Features</h2>
        <div class="grid grid-cols-3 gap-8 max-md:grid-cols-1 max-md:gap-12">
          <div class="flex flex-col items-center text-center">
            <img src="/screenshots/IMG_4562.PNG" alt="Explore the map" class="w-full max-w-55 rounded-3xl shadow-[0_16px_48px_rgba(0,0,0,0.2)] mb-6" />
            <h3 class="text-[17px] font-semibold text-neutral-900 dark:text-neutral-100 mb-2 tracking-[-0.01em]">Explore the Map</h3>
            <p class="text-[14px] leading-[1.6] text-neutral-500 dark:text-neutral-400">See where your friends have been eating and what they thought. Browse pins on a live map.</p>
          </div>
          <div class="flex flex-col items-center text-center">
            <img src="/screenshots/IMG_4561.PNG" alt="Leave reviews" class="w-full max-w-55 rounded-3xl shadow-[0_16px_48px_rgba(0,0,0,0.2)] mb-6" />
            <h3 class="text-[17px] font-semibold text-neutral-900 dark:text-neutral-100 mb-2 tracking-[-0.01em]">Leave Reviews</h3>
            <p class="text-[14px] leading-[1.6] text-neutral-500 dark:text-neutral-400">Drop a review for any restaurant or food spot. Share your honest take with your circle.</p>
          </div>
          <div class="flex flex-col items-center text-center">
            <img src="/screenshots/IMG_4559.PNG" alt="Friend recommendations" class="w-full max-w-55 rounded-3xl shadow-[0_16px_48px_rgba(0,0,0,0.2)] mb-6" />
            <h3 class="text-[17px] font-semibold text-neutral-900 dark:text-neutral-100 mb-2 tracking-[-0.01em]">Friend Recommendations</h3>
            <p class="text-[14px] leading-[1.6] text-neutral-500 dark:text-neutral-400">Follow friends and see their picks. Trustworthy recs from people you actually know.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="py-8 px-11 bg-white dark:bg-black text-center max-md:py-15 max-md:px-5.5">
      <div class="max-w-250 mx-auto">
        <h2 class="text-[clamp(24px,4vw,36px)] font-bold tracking-[-0.02em] text-neutral-900 dark:text-neutral-100 mb-4">Ready to try it?</h2>
        <p class="text-[17px] text-neutral-500 dark:text-neutral-400 mb-8 leading-[1.6]">Join the beta and help shape the app. Your feedback makes a real difference.</p>
        <img src="/app_icons/WOM_logo.png" alt="Word O' Mouth logo" class="block mx-auto mb-4 w-32 h-32 rounded-2xl shadow-[0_4px_16px_rgba(0,0,0,0.12)]" />
        <a
          href="https://testflight.apple.com/join/WVu7u7ED"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-block bg-neutral-900 text-white dark:bg-neutral-100 dark:text-black text-[15px] font-semibold py-3.5 px-8 rounded-full no-underline tracking-[-0.01em] hover:opacity-80"
        >
          Join the Beta on TestFlight
        </a>
      </div>
    </section>

    <FooterSection name="Edwin Salcedo" email="edwin.a.salcedo02@gmail.com" />
  </div>
</template>

<script>
import FooterSection from '@/components/FooterSection.vue'

export default {
  name: 'WomLandingView',
  components: {
    FooterSection
  }
}
</script>

<style scoped>
/* ── Hero logo watermark (kept for --hero-logo-size CSS variable) ── */
.hero-logo-bg {
  --hero-logo-size: 420px;
  position: absolute;
  width: var(--hero-logo-size);
  height: var(--hero-logo-size);
  object-fit: contain;
  top: 50%;
  transform: translateY(-50%);
  opacity: 0.15;
  border-radius: 28%;
  pointer-events: none;
  z-index: 0;
}

/* ── Fan layout (kept for complex chained transforms) ── */
.hero-inner {
  gap: 256px;
}

.fan-container {
  width: 260px;
  height: 520px;
}

.fan-img {
  position: absolute;
  width: 220px;
  border-radius: 28px;
  box-shadow: 0 16px 48px rgba(0, 0, 0, 0.2);
  top: 50%;
  left: 50%;
  transform-origin: bottom center;
}

.fan-left  { transform: translate(-50%, -50%) translateX(-60px) rotate(-12deg); z-index: 1; }
.fan-center { transform: translate(-50%, -50%) rotate(0deg); z-index: 3; }
.fan-right  { transform: translate(-50%, -50%) translateX(60px) rotate(12deg); z-index: 2; }

@media (max-width: 768px) {
  .hero-inner { gap: 40px; }

  .fan-container {
    width: 200px;
    height: 400px;
  }

  .fan-img { width: 170px; }

  .fan-left  { transform: translate(-50%, -50%) translateX(-48px) rotate(-12deg); }
  .fan-right { transform: translate(-50%, -50%) translateX(48px) rotate(12deg); }
}
</style>
