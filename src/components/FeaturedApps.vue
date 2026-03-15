<template>
  <div class="grid grid-cols-3 gap-5 mt-10 max-md:grid-cols-1">
    <div
      v-for="(app, index) in apps"
      :key="index"
    >
      <AppCard
        :icon="app.icon"
        :title="app.name"
        :subtitle="app.description"
        :to="app.link"
        :external="app.external !== false"
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
