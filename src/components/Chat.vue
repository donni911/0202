<template>
  <section>
    <div class="flex items-center py-4 px-4">
      <h3 class="font-bold mr-2">Latest reviews</h3>
      <button
        class="p-0 bg-transparent inline-block text-[#005DA1] underline mr-auto"
      >
        All reviews
      </button>
      <div class="grid gap-4 grid-cols-2">
        <div class="flex items-center">
          <div class="mr-1">
            <Icon :name="'like'" />
          </div>
          <span>131</span>
        </div>
        <div class="flex items-center">
          <div class="mr-1">
            <Icon :name="'comment'" />
          </div>
          <span>14</span>
        </div>
      </div>
    </div>
    <messages />
  </section>
</template>


<script>
import Icon from "./Icon.vue";

import Messages from "./Messages.vue";

export default {
  components: {
    Icon,
    Messages,
  },
};
</script>