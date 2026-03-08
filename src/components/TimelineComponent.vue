<template>
  <div class="timeline relative pl-10">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="timeline-item relative mb-12 pl-6"
    >
      <h3 class="text-[24px] font-semibold mb-1 tracking-[-0.01em] text-neutral-900 dark:text-neutral-100">{{ item.title }}</h3>
      <p class="text-[17px] text-neutral-500 dark:text-neutral-400 mb-1">{{ item.company }}</p>
      <p class="text-[14px] text-neutral-500 dark:text-neutral-500 mb-3">{{ item.date }}</p>
      <p class="text-[17px] leading-normal text-neutral-500 dark:text-neutral-500 whitespace-pre-line">{{ item.description }}</p>
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
/* Vertical line */
.timeline::before {
  content: '';
  position: absolute;
  left: 8px;
  top: 0;
  bottom: 0;
  width: 2px;
  background-color: #e5e5e5; /* neutral-200 */
}

.dark .timeline::before {
  background-color: #262626; /* neutral-800 */
}

/* Dot per item */
.timeline-item::before {
  content: '';
  position: absolute;
  left: -39px;
  top: 4px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border-width: 3px;
  border-style: solid;
  background-color: #0071e3; /* accent */
  border-color: white;
}

.dark .timeline-item::before {
  border-color: black;
}
</style>
