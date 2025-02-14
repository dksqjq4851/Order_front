<template>
<h1>store componentA</h1>
<p>일반변수값 count : {{ count }}</p>
<v-btn @click="incrementCount">count값 증가</v-btn>
<p>store변수값 count : {{ getStoreCount }}</p>
<v-btn @click="incrementStoreCount">store count값 증가</v-btn>
<input type="text" v-model="message">
<v-btn @click="updateMessage">message전송</v-btn>
</template>
<script>
    export default{
        data(){
            return{
                count:0,
                message:""
            }
        },
        computed:{
            getStoreCount(){
                return this.$store.getters.getCount;
            },


        },
        methods:{
            incrementCount(){
                this.count++
            },
            incrementStoreCount(){
                // vuex에서 actions를 호출할때는 dispatch를 사용
                this.$store.dispatch('increment')
            },
            updateMessage(){
                this.$store.dispatch('updateMessage', this.message)
            }
        }
    }
</script>