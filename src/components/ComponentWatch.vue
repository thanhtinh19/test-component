<template>
    <div>
        <input type="text" v-model="message"/>
        <p v-if="isTyping">Typing...</p>
        <br/>
        <br/>
        <br/>
        <br/>
        GB: <input type="number" v-model.number="gb"/>
        MB: <input type="number" v-model.number="mb"/>
    </div>
</template>
<script>
export default {
    data(){
        return{
            message:'',
            isTyping: false,
            gb: null,
            mb:null
        }
    },
    watch:{
        message(newValue, oldValue){
            console.log('New Value ' + newValue)
            console.log('Old Value ' + oldValue)
            this.isTyping = true
            setTimeout(() => {
                this.isTyping = false
            }, 2000)
        },
        gb(value){
            this.mb = value * 1024
        },
        mb(value){
            this.gb = value / 1024
        }
    }
}
</script>
<style scoped>

</style>