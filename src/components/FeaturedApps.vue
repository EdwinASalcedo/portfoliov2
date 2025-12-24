<template>
  <div class="featured-grid">
    <div
      v-for="(app, index) in apps"
      :key="index"
      class="fade-in"
      :style="{ animationDelay: (index * 0.1) + 's' }"
    >
      <AppCard
        :icon="app.icon"
        :title="app.name"
        :subtitle="app.description"
        :to="app.link"
        :external="true"
      />
    </div>
  </div>
</template>

<script>
import AppCard from './AppCard.vue'

export default {
  name: 'FeaturedApps',
  components: {
    AppCard
  },
  props: {
    apps: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.featured-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin-top: 40px;
}

@media (max-width: 768px) {
  .featured-grid {
    grid-template-columns: 1fr;
  }
}
</style>