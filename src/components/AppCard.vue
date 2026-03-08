<template>
  <div class="flex items-center gap-4 p-4">
    <img :src="icon" :alt="title" class="w-24 h-24 rounded-3xl shrink-0" />
    <div class="flex-1 min-w-0">
      <h4 class="text-base font-semibold mb-1 text-neutral-900 dark:text-neutral-100 wrap-break-word">{{ title }}</h4>
      <p class="text-[14px] text-neutral-500 dark:text-neutral-400 mb-2 line-clamp-2">{{ subtitle }}</p>
      <button
        class="bg-[#007aff] text-white border-none rounded-full px-4 py-2 text-[14px] font-semibold cursor-pointer hover:bg-[#0051d5]"
        @click="handleClick"
      >View</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppCard',
  props: {
    icon: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
    to: {
      type: String,
      required: false,
    },
    external: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleClick() {
      if (this.external) {
        window.open(this.to, '_blank')
      } else if (this.to) {
        this.$router.push(this.to)
      }
    },
  },
}
</script>
