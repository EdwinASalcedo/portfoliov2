<template>
  <div class="timeline">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="timeline-item mb-12"
    >
      <!-- Header row: info left, logo right -->
      <div class="flex items-center gap-2">
        <div class="w-80 shrink-0 max-md:w-auto">
          <h3 class="text-[28px] font-semibold mb-1 tracking-[-0.01em] text-neutral-900 dark:text-neutral-100">{{ item.title }}</h3>
          <p class="text-[19px] text-neutral-900 dark:text-neutral-100 mb-1">{{ item.company }}</p>
          <p class="text-[15px] text-neutral-900 dark:text-neutral-100 mb-3">{{ item.date }}</p>
        </div>
        <img v-if="item.logo" :src="item.logo" :alt="item.company" :class="item.logoClass" class="max-h-20 w-auto object-contain shrink-0 opacity-90 max-md:hidden" />
      </div>

      <template v-if="collapsible">
        <button
          class="text-[14px] text-accent font-medium mb-2 cursor-pointer bg-transparent border-none p-0 hover:opacity-80"
          @click="toggle(index)"
        >{{ expanded[index] ? 'Show less' : 'Show more' }}</button>
        <p v-show="expanded[index]" class="text-[18px] leading-normal text-neutral-900 dark:text-neutral-100 whitespace-pre-line mt-1">{{ item.description }}</p>
      </template>
      <p v-else class="text-[18px] leading-normal text-neutral-500 dark:text-neutral-500 whitespace-pre-line">{{ item.description }}</p>
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
    },
    collapsible: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      expanded: []
    }
  },
  created() {
    this.expanded = this.items.map(() => false)
  },
  methods: {
    toggle(index) {
      this.expanded[index] = !this.expanded[index]
    }
  }
}
</script>

<style scoped>
</style>
