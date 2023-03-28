<template>
  <div class="w-full relative">
    <div
      class="bg-red-100 rounded-r absolute top-0 left-0 bottom-0 z-0 isolate"
      :style="{ right: computedBar, background: backgroundType }"
    ></div>
    <div class="p-2 flex justify-between">
      <span class="text-sm z-10">{{ service.type }}</span>
      <span class="text-sm z-10 font-bold">{{ service.amount }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    service: {
      required: true,
      type: Object,
    },
    type: {
      required: true,
      type: String,
    },
  },
  computed: {
    computedBar() {
      return 100 - Math.round((100 / 15) * this.service.amount) + "%";
    },

    backgroundType() {
      switch (this.type) {
        case "primary":
          return "#ACE2F8";
        case "success":
          return "#B1E19B";
      }
    },
  },
};
</script>


