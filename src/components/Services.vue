<template>
  <div class="w-[75%] ml-auto">
    <h5 class="text-sm te px-5 py-2 text-right">Services</h5>
    <div class="border-t-2 border-b-2 border-[#DADADA] py-4 pr-10">
      <div class="grid gap-[2px] border-l-2 border-l-[#33333333]">
        <progress-bar type="success" :service="services[0]" />
        <progress-bar type="primary" :service="services[1]" />
        <progress-bar type="primary" :service="services[2]" />
      </div>
    </div>
    <div class="pt-4 flex justify-between pr-10">
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

  mounted() {
    console.log(this.services[0]);
  },
};
</script>