<template>
  <div class="py-2">
    <div class="flex items-baseline mb-2">
      <h5 class="font-bold mr-2 text-sm">{{ message.name }}</h5>
      <span class="text-xs text-[#808080]">{{ computedTime }}</span>
    </div>

    <div
      class="relative c-message-triangle py-3 px-5 bg-[#F2FBFF] border-2 border-[#E5E5E5] shadow-[0px_4px_10px_rgba(128,128,128,0.2)]"
    >
      <p class="text-left text-sm">{{ message.message }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      required: true,
      type: Object,
    },
  },

  computed: {
    computedTime() {
      let date = new Date(this.message.date);

      return date.toLocaleDateString("en-GB", {
        day: "numeric",
        month: "short",
        year: "numeric",
      });
    },
  },
};
</script>

<style>
.c-message-triangle {
  @apply before:absolute before:bottom-[100%] before:left-6 before:content-[''] before:border-b-[10px] before:border-b-[#E5E5E5] before:border-r-[10px] before:border-r-[transparent] after:absolute after:bottom-[100%] after:left-6 after:content-[''] after:border-b-[8px] after:border-b-[#F2FBFF] after:border-r-[8px] after:border-r-[transparent] after:translate-x-[1.5px] after:translate-y-[2px];
}
</style>