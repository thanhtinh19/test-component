<template>
  <div class="parent-component">
    <div class="form">
        <form>
          <h1>{{content}}</h1>
          <input type="text" v-model="message"> 
          <button type="submit" @click="send()">Send</button>
          <p v-if="messageDeleted">Bạn đã xóa {{messageDeleted}}</p>
    </form>
    </div>
  <ComponentChildVue v-bind:message="messages" v-on:notify-delete-message="listenDelete"/>
  </div>
</template>

<script>
import ComponentChildVue from './ComponentChild.vue'
export default {
  components: {
    ComponentChildVue,
    },
    data(){
      return{
        content: 'Parent Component',
        message: '',
        messages: [],
        messageDeleted: '',
        gender: 1,
      }
    },
    created(){
      this.getLS()
    },
    mouted(){
      this.listenDelete()
    },

    methods:{
      send(){
        if(this.message != ''){
        this.messages.push(this.message)
         this.setLS() 
        }
        this.message = ''
      },
      setLS(){
        localStorage.setItem('messages', JSON.stringify(this.messages))
      },
      getLS(){  
        this.messages = JSON.parse(localStorage.getItem("messages"));
      },
      listenDelete(message){
        this.messageDeleted = message
        var v = this
        const messageDeletedInterval = setInterval(() => {
          v.messageDeleted = ''
        }, 2000) 
        clearInterval(messageDeletedInterval)
      },
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.parent-component{
  display: flex;
}
  input{
    margin-right: 10px;
    padding: 5px;
  }
  button{
    padding: 7px;
    background-color: aquamarine;
    cursor: pointer;
    border-radius: 5px;
    border: none;
  }
  button:hover{
    background-color: rgb(8, 169, 169);
  }

  form{
    background-color: rgba(169, 169, 169, 0.37);
    margin-right: 30px;
    padding: 20px;
  }
  .form p{
    color: red;
  }
</style>
