<template>
  <div class="card-grid">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="card fade-in"
      :class="{ 'card-secondary': cardBg === 'secondary' }"
      :style="{ animationDelay: (index * 0.1) + 's' }"
    >
      <h3 class="card-title">{{ item.title }}</h3>
      <p class="card-subtitle" v-if="item.subtitle">{{ item.subtitle }}</p>
      <p class="card-meta" v-if="item.date">{{ item.date }}</p>
      <p class="card-description">{{ item.description }}</p>
      <div class="card-tags" v-if="item.tags">
        <span 
          v-for="tag in item.tags" 
          :key="tag"
          class="tag"
        >
          {{ tag }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardGrid',
  props: {
    items: {
      type: Array,
      required: true
    },
    cardBg: {
      type: String,
      default: 'primary',
      validator: (value) => ['primary', 'secondary'].includes(value)
    }
  }
}
</script>

<style scoped>
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
  margin-top: 40px;
}

.card {
  background: var(--bg-primary);
  border-radius: 18px;
  padding: 32px;
  border: 1px solid var(--border);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 4px 6px var(--card-shadow);
}

.card.card-secondary {
  background: var(--bg-secondary);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 24px var(--card-shadow);
}

.card-title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 8px;
  letter-spacing: -0.01em;
}

.card-subtitle {
  font-size: 17px;
  color: var(--text-secondary);
  margin-bottom: 4px;
  font-weight: 400;
}

.card-meta {
  font-size: 14px;
  color: var(--text-tertiary);
  margin-bottom: 16px;
}

.card-description {
  font-size: 17px;
  line-height: 1.5;
  color: var(--text-tertiary);
  white-space: pre-line;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 16px;
}

.tag {
  background: var(--bg-secondary);
  color: var(--text-secondary);
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 13px;
  font-weight: 400;
}

@media (max-width: 768px) {
  .card-grid {
    grid-template-columns: 1fr;
  }
}
</style>