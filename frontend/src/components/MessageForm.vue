<template>
  <div>
    <h1>Send a Message</h1>
    <form @submit.prevent="submitMessage">
      <input type="text" v-model="messageText" placeholder="Enter your message" required />
      <button type="submit">Submit</button>
    </form>
    <p v-if="responseMessage">{{ responseMessage }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MessageForm',
  data() {
    return {
      messageText: '',
      responseMessage: '',
    };
  },
  methods: {
    async submitMessage() {
      try {
        const response = await axios.post('http://localhost:8000/api/messages/', {
          text: this.messageText,
        });
        this.responseMessage = 'Message sent successfully!';
        this.messageText = '';
      } catch (error) {
        console.error(error);
        this.responseMessage = 'Failed to send message.';
      }
    },
  },
};
</script>

<style scoped>
/* Add some basic styling */
</style>
