<template>
  <div class="h-full">
    <div
      class="pb-5 h-[350px] overflow-y-auto overflow-x-hidden px-4"
      ref="messagesBox"
    >
      <TransitionGroup name="list" tag="ul">
        <message
          v-for="message in messagesData"
          :message="message"
          :key="message.name"
        />
      </TransitionGroup>
    </div>
    <div class="bg-[#F2F2F2] pt-7 px-4 h-full pb-5 relative">
      <p
        v-if="error"
        class="text-[red] text-xs absolute top-2 left-2/4 -translate-x-2/4"
      >
        Type more than 3 characters
      </p>
      <input
        type="text"
        class="p-4 mb-6 w-full bg-white rounded border-2 border-[#000]"
        placeholder="Type a message..."
        v-model="inputMessage"
        @keydown.enter.prevent="submitOnEnter"
      />
      <button
        class="bg-[#FDD639] text-[#33333] p-3 rounded-full font-bold min-w-[280px] active:scale-90 transition-transform"
        @click="send"
      >
        Send a message
      </button>
    </div>
  </div>
</template>

<script>
import Message from "./Message.vue";

export default {
  components: {
    Message,
  },

  data() {
    return {
      inputMessage: "",
      error: false,
    };
  },

  inject: {
    messagesData: {
      required: true,
      type: Array,
    },
  },

  methods: {
    send() {
      if (this.inputMessage.length < 3) {
        this.error = true;
        return;
      }

      this.error = false;

      const newMessage = {
        id: Math.random().toString(16).slice(2),
        name: "Me",
        message: this.inputMessage,
        date: new Date().getTime(),
      };

      this.inputMessage = "";

      this.messagesData.push(newMessage);

      this.$nextTick(() => {
        const messagesBox = this.$refs.messagesBox;
        messagesBox.scrollTop = messagesBox.scrollHeight;
      });
    },

    submitOnEnter(event) {
      if ((event.metaKey || event.ctrlKey) && event.keyCode === 13) {
        this.send();
        console.log(this.messagesData);
      }
    },
  },
};
</script>

<style>
.list-move,
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

.list-leave-active {
  position: absolute;
}
</style>