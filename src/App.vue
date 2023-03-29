
<template>
  <div class="w-full h-full sm:w-[490px] border-2 overflow-hidden">
    <person-info :user="userInfo.user" />
    <chat />
  </div>
</template>

<script>
import user from "./data/user.json";
import messages from "./data/messages.json";

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
      messagesData: messages,
    };
  },
  provide() {
    return {
      messagesData: this.messagesData.messages,
    };
  },
};
</script>
