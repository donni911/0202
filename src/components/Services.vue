<template>
  <div class="w-[75%] ml-auto px-4">
    <h5 class="text-sm te px-5 py-2 text-right">Services</h5>
    <div class="border-t-2 border-b-2 border-[#DADADA] py-4 pr-8">
      <div class="grid gap-[2px] border-l-2 border-l-[#33333333]">
        <progress-bar type="success" :service="services[0]" />
        <progress-bar type="primary" :service="services[1]" />
        <progress-bar type="primary" :service="services[2]" />
      </div>
    </div>
    <div class="pt-4 flex justify-between pr-8">
      <span class="font-bold">Total</span>
      <span class="font-bold">15</span>
    </div>
  </div>
</template>

<script>
import ProgressBar from "./UI/ProgressBar.vue";

export default {
  components: {
    ProgressBar,
  },
  props: {
    services: {
      required: true,
      type: Array,
    },
  },
};
</script>