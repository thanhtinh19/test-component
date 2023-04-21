<template>
  <div class="list">
    <h1>Childrent Component</h1>
    <ul>
      <div class="list-item" v-for="(mess, index) in message" :key="mess">
      <li >{{mess}}</li>
      <a href="" @click="deleteMessage(index)">Delete</a>
    </div>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    message:[]
  },
  data(){
    return{
        messageTmp: this.message,
    }
  },
  methods:{
    deleteMessage(index){
        this.$emit('notify-delete-message', this.messageTmp[index])
        this.messageTmp.splice(index,1)
        localStorage.setItem('messages', JSON.stringify(this.messageTmp))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .list{
        padding: 0;
        margin: 0;
        background-color: rgba(169, 169, 169, 0.37);
        padding: 20px;
        
      }
      ul{
        margin: 0;
        padding: 0;
        position: sticky;
        height: 40vh;
        overflow: auto;
      }
    li{
        list-style: none;
    }
    a{
        text-decoration: none;
        background: red;
        color: white;
        padding: 5px;
        border-radius:5px ;
        font-size: 13px;
    }
    a:hover{
      background: rgb(226, 5, 5);
    }
    .list-item{
      display: flex;
      justify-content: space-between;
      background-color: white;
      padding: 10px;
      align-items: center;
      margin-bottom: 10px;
      font-size: 15px;

    }

</style>