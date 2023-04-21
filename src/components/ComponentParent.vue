<template>
  <div class="parent-component">
    <div class="form">
        <form v-on:submit.prevent = "send()">
          <h1>{{content}}</h1>
          <input type="text" v-model="message"> 
          <button type="submit">Send</button>
          <p v-if="isDeleted">Bạn đã xóa {{messageDeleted}}</p>
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
        isDeleted:false,
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
        this.isDeleted = true  
      },
    },
    watch:{
      isDeleted(newVal){
        if(newVal){
          setTimeout(()=>{
            this.isDeleted = false
          }, 5000)
        }
        if(!newVal){
          clearInterval(this.isDeleted)
        }
      }
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
