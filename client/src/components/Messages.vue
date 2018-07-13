<template>
  <div>
    <input type="text" placeholder="Enter message" v-model="text" @keyup.enter="createMessage">
    <button type="submit" @click="createMessage">Add message</button>
    <ul>
      <li v-for="message in messages" :key="message._id">
        <span>{{ message.text }}</span>
        <span @click="removeMessage(message)">x</span>
      </li>
    </ul>
  </div>
</template>

<script>
  // mapState, 
  import { mapGetters, mapActions } from 'vuex';

  export default {
    name: 'Messages',
    components: {
    },
    data () {
      return {
        text: ''
      }
    },
    mounted() {
      this.findMessages({ query: {} });
    },
    methods: {
      ...mapActions('messages', { findMessages: 'find' }),
      async createMessage() {
        const { Message } = this.$FeathersVuex;
        const newMessage = new Message({text: this.text});
        await newMessage.save();
      },
      async removeMessage(message) {
        await message.remove();
      },
      async onCreateMessage() {
          await this.createMessage(this.message);
          this.text = '';
      },
    },
    computed: {
      ...mapGetters('messages', { findMessagesInStore: 'find' }),
      messages() {
        return this.findMessagesInStore().data;
      }
    },
  };
</script>
