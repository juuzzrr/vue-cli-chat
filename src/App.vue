<template>
  <div id="app">
    <Container>
      <ChatWindow v-on:send-message="sendmessage">
        <ChatMessage v-for="(mesasage, i) in messages"
        :key="i">
        </ChatMessage>
      </ChatWindow>
    </Container>
  </div>
</template>


<script>
import ChatMessage from './components/ChatMessage.vue'
import Container from './components/Container.vue'
import ChatWindow from './components/ChatWindow.vue'
export default {
  name: 'App',
  components: {
    Container,
    ChatMessage,
    ChatWindow
  },
  data(){
    return{
      messages:[
        {username:'', text:''}
      ]
    }
  },
  methods:{
    getUserData(){
      this.axios.get("http://37.77.104.246/api/chat/getmessages.php")
      .then( (response)=>{
          this.username=response.data.author;
          this.text=response.data.text;
          this.datetime=response.data.datetime;
        }
    )
  },
  putUserData(){
    this.axios.post('http://37.77.104.246/api/chat/sendmessage.php', {
      author : this.username,
      text : this.text
    })
    .then((response) => {
      cpnsole.log(response);
    })
  },
  sendmessage(){
    this.messages.push({
      text: this.text,
      author: this.username,
    })
  }
},
mounted(){
  this.getUserData();
  this.putUserData();
}
};
</script>

<style>

body {
  margin: 0;
  background-color: #f9f9fa;
}

</style>
