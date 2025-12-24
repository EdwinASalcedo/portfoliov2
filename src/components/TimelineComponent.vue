<template>
  <div class="timeline">
    <div 
      v-for="(item, index) in items" 
      :key="index"
      class="timeline-item fade-in"
      :style="{ animationDelay: (index * 0.1) + 's' }"
    >
      <h3 class="timeline-title">{{ item.title }}</h3>
      <p class="timeline-subtitle">{{ item.company }}</p>
      <p class="timeline-date">{{ item.date }}</p>
      <p class="timeline-description">{{ item.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TimelineComponent',
  props: {
    items: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.timeline {
  position: relative;
  padding-left: 40px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 8px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--border);
}

.timeline-item {
  position: relative;
  margin-bottom: 48px;
  padding-left: 24px;
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: -39px;
  top: 4px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--accent);
  border: 3px solid var(--bg-primary);
}

.timeline-title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 4px;
  letter-spacing: -0.01em;
}

.timeline-subtitle {
  font-size: 17px;
  color: var(--text-secondary);
  margin-bottom: 4px;
}

.timeline-date {
  font-size: 14px;
  color: var(--text-tertiary);
  margin-bottom: 12px;
}

.timeline-description {
  font-size: 17px;
  line-height: 1.5;
  color: var(--text-tertiary);
  white-space: pre-line;
}
</style>