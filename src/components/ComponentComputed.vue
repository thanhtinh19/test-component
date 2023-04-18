<template>
    <div>
        <!-- <p>{{genderRender}}</p>
        <button @click="changeGender()">Change Gender</button> -->
        <div class="number">
            <div class="NumberA">
                <p>a: {{AddA}}</p>
                <button @click="stateA++">a + 1</button>
            </div>
            <div class="NumberB">
                <p>b: {{AddB}}</p>
                <button @click="stateB++">b + 1</button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
            gender: 1,
            stateA: 0,
            stateB: 0
        }
    },
    methods:{
        changeGender(){
            console.log('changed')
            if(this.gender === 1){
                this.gender = 2
            }
        //    else this.gender = 1
        },
        // AddA(){
        //     console.log('Add a')
        //     return this.stateA            
        // },
        // AddB(){
        //     console.log('Add b')
        //     return this.stateB
        // }
    },
    computed: {
        genderRender(){
            console.log('re-render')
            return this.gender === 1 ? 'Nam' : 'Nữ'
        },
        AddA(){
            console.log('Add a')
            return this.stateA            
        },
        AddB(){
            console.log('Add b')
            return this.stateB
        }
    }
}
</script>
<style scoped>
    .number{
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }
    p{
        text-align: center;
    }

</style>