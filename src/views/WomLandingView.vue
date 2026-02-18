<template>
  <div class="wom-landing">

    <!-- Hero: screenshot left, text right -->
    <section class="hero">
      <div class="hero-inner">
        <div class="hero-screenshot">
          <div class="fan-container">
            <img src="/screenshots/IMG_4562.PNG" alt="App screenshot" class="fan-img fan-left" />
            <img src="/screenshots/IMG_4558.PNG" alt="App screenshot" class="fan-img fan-center" />
            <img src="/screenshots/IMG_4559.PNG" alt="App screenshot" class="fan-img fan-right" />
          </div>
        </div>
        <div class="hero-text">               
          <h1 class="app-name">Word O' Mouth</h1>
          <p class="app-tagline">Never have food FOMO again</p>
          <p class="app-description">
            Explore food recommendations from friends on the map, or leave reviews of your own. 
            Discover your next favorite spot through people you trust. 
            Enjoy the look of Apple Liquid Glass through iOS 26
          </p>
          <a
            href="https://testflight.apple.com/join/WVu7u7ED"
            target="_blank"
            rel="noopener noreferrer"
            class="btn-testflight"
          >
            Join the Beta on TestFlight
          </a>
          <p class="testflight-note">Requires iOS 26</p>
        </div>
      </div>
    </section>

    <!-- Features: 3 screenshots with captions below -->
    <section class="features">
      <div class="section-content">
        <h2 class="section-title">Features</h2>
        <div class="feature-grid">
          <div class="feature-card">
            <img src="/screenshots/IMG_4562.PNG" alt="Explore the map" class="feature-screenshot" />
            <h3>Explore the Map</h3>
            <p>See where your friends have been eating and what they thought. Browse pins on a live map.</p>
          </div>
          <div class="feature-card">
            <img src="/screenshots/IMG_4561.PNG" alt="Leave reviews" class="feature-screenshot" />
            <h3>Leave Reviews</h3>
            <p>Drop a review for any restaurant or food spot. Share your honest take with your circle.</p>
          </div>
          <div class="feature-card">
            <img src="/screenshots/IMG_4559.PNG" alt="Friend recommendations" class="feature-screenshot" />
            <h3>Friend Recommendations</h3>
            <p>Follow friends and see their picks. Trustworthy recs from people you actually know.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="cta">
      <div class="section-content">
        <h2>Ready to try it?</h2>
        <p>Join the beta and help shape the app. Your feedback makes a real difference.</p>
        <img src="/app_icons/WOM_logo.png" alt="Word O' Mouth logo" class="app-icon" />     
        <a
          href="https://testflight.apple.com/join/WVu7u7ED"
          target="_blank"
          rel="noopener noreferrer"
          class="btn-testflight"
        >
          Join the Beta on TestFlight
        </a>
        <p class="testflight-note">
          Have feedback? Reach out at
          <a href="mailto:edwin.a.salcedo02@gmail.com">edwin.a.salcedo02@gmail.com</a>
        </p>
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
.wom-landing {
  padding-top: 0px;
}

/* ── Hero ─────────────────────────────────────────── */
.hero {
  min-height: 50vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 44px 60px;
  background: var(--bg-primary);
}

.hero-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
  max-width: 1000px;
  width: 100%;
}

.hero-screenshot {
  display: flex;
  justify-content: center;
  align-items: center;
}

.fan-container {
  position: relative;
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

.fan-left {
  transform: translate(-50%, -50%) translateX(-60px) rotate(-12deg);
  z-index: 1;
}

.fan-center {
  transform: translate(-50%, -50%) rotate(0deg);
  z-index: 3;
}

.fan-right {
  transform: translate(-50%, -50%) translateX(60px) rotate(12deg);
  z-index: 2;
}

.hero-text {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  text-align: left;
}

.app-icon {
  display: block;
  margin: 0 auto 16px;
  width: 128px;
  height: 128px;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
}

.app-name {
  font-size: clamp(32px, 5vw, 52px);
  font-weight: 700;
  letter-spacing: -0.03em;
  color: var(--text-primary);
  margin-bottom: 10px;
}

.app-tagline {
  font-size: clamp(16px, 2.5vw, 22px);
  font-weight: 500;
  color: var(--text-secondary, #6e6e73);
  margin-bottom: 16px;
}

.app-description {
  font-size: 16px;
  line-height: 1.65;
  color: var(--text-secondary, #6e6e73);
  margin-bottom: 32px;
}

.btn-testflight {
  display: inline-block;
  background: var(--text-primary);
  color: var(--bg-primary);
  font-size: 15px;
  font-weight: 600;
  padding: 14px 32px;
  border-radius: 980px;
  text-decoration: none;
  transition: opacity 0.2s ease, transform 0.2s ease;
  letter-spacing: -0.01em;
}

.btn-testflight:hover {
  opacity: 0.8;
  transform: translateY(-2px);
}

.testflight-note {
  margin-top: 12px;
  font-size: 13px;
  color: var(--text-secondary, #6e6e73);
}

.testflight-note a {
  color: var(--text-primary);
  text-decoration: underline;
}

/* ── Features ─────────────────────────────────────── */
.features {
  padding: 32px 44px;
  background: var(--bg-secondary);
}

.section-content {
  max-width: 1000px;
  margin: 0 auto;  
}

.section-title {
  font-size: clamp(24px, 4vw, 36px);
  font-weight: 700;
  letter-spacing: -0.02em;
  color: var(--text-primary);
  text-align: center;
  margin-bottom: 48px;
}

.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
}

.feature-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.feature-screenshot {
  width: 100%;
  max-width: 220px;
  border-radius: 24px;
  box-shadow: 0 16px 48px rgba(0, 0, 0.5);
  margin-bottom: 24px;
}

.feature-card h3 {
  font-size: 17px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 8px;
  letter-spacing: -0.01em;
}

.feature-card p {
  font-size: 14px;
  line-height: 1.6;
  color: var(--text-secondary, #6e6e73);
}

/* ── CTA ──────────────────────────────────────────── */
.cta {
  padding: 32px 44px;
  background: var(--bg-primary);
  text-align: center;
}

.cta h2 {
  font-size: clamp(24px, 4vw, 36px);
  font-weight: 700;
  letter-spacing: -0.02em;
  color: var(--text-primary);
  margin-bottom: 16px;
}

.cta p {
  font-size: 17px;
  color: var(--text-secondary, #6e6e73);
  margin-bottom: 32px;
  line-height: 1.6;
}

/* ── Responsive ───────────────────────────────────── */
@media (max-width: 768px) {
  .hero {
    padding: 60px 22px 48px;
  }

  .hero-inner {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
  }

  .hero-text {
    align-items: center;
  }

  .fan-container {
    width: 200px;
    height: 400px;
  }

  .fan-img {
    width: 170px;
  }

  .fan-left {
    transform: translate(-50%, -50%) translateX(-48px) rotate(-12deg);
  }

  .fan-right {
    transform: translate(-50%, -50%) translateX(48px) rotate(12deg);
  }

  .feature-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .features,
  .tech-stack,
  .cta {
    padding: 60px 22px;
  }
}
</style>
