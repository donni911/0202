<template>
  <header class="flex">
    <div class="w-[25%] mr-5">
      <div class="relative rounded-full w-[124px] h-[124px]">
        <img
          :src="computedImage"
          :alt="user.fullName"
          class="absolute inset-0 z-10"
        />
      </div>
    </div>
    <div class="w-[75%] flex flex-col items-start justify-center z-0">
      <h1 class="text-base font-bold">{{ user.fullName }}</h1>
      <h4 class="text-sm text-[#808080]">{{ user.position }}</h4>
      <div
        class="w-[110%] -translate-x-[10%] pl-[10%] py-1 bg-[#FFFBC8] border-2 border-[#dadada] rounded"
      >
        <p class="text-sm max-w-[200px] leading-5 text-left">
          {{ user.quote }}
        </p>
      </div>
    </div>
  </header>
  <services :services="user.services" />
</template>

<script>
import Services from "./Services.vue";

export default {
  components: {
    Services,
  },

  props: {
    user: {
      required: true,
      type: Object,
    },
  },

  computed: {
    computedImage() {
      return new URL(`/src/assets/img/${this.user.image}`, import.meta.url)
        .href;
    },
  },
};
</script>