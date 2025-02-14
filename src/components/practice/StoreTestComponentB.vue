<template>
    <h1>store componentB</h1>
    <p>일반변수값 count : {{ count }}</p>
    <p>store변수값 count : {{ getStoreCount }}</p>
    <input type="text" v-model="getMessage">
    </template>
    <script>
        export default{
            data(){
                return{
                    count: 5
                }
            },
            computed:{
            getStoreCount(){
                return this.$store.getters.getCount;
            },
            getMessage(){
                return this.$store.getters.getMessage
            }
            
        }
    }
    </script>