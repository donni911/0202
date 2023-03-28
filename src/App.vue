
<template>
  <div
    class="w-full h-full py-5 px-4 md:w-[490px] md:h-[900px] border-2 overflow-hidden"
  >
    <person-info :user="userInfo.user" />
    <chat />
  </div>
</template>

<script>
import user from "./data/user.json";

import PersonInfo from "./components/PersonInfo.vue";
import Chat from "./components/Chat.vue";
export default {
  components: {
    PersonInfo,
    Chat,
  },
  data() {
    return {
      userInfo: user,
    };
  },
  mounted() {
    console.log(this.userInfo);
  },
};
</script>
