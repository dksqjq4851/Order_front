<template>
    <h1>vue 조건식</h1>
    <button v-if="!isLogined" @click="login">로그인</button>
    <button v-if="isLogined" @click="logout">로그아웃</button><br><br>
    <div v-if="!isLogined">로그인해주세요</div>
    <div v-if="isLogined">환영합니다 고갱님</div>

    <h1>상품목록조회</h1>
    <v-simple-table>
        <thead>
            <tr>
                <th>id</th>
                <th>이름</th>
                <th>가격</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="product in productList" :key="product.id">
                <td>{{product.id}}</td><td>{{product.name}}</td><td>{{product.price}}</td>
            </tr>
        </tbody>
    </v-simple-table>
    
</template>
<script>
import axios from 'axios';
export default{
    data(){
        return{
            isLogined:false,
            productList:[{id:1, name:"apple", price:30000},{id:2, name:"banana", price:3000},{id:3, name:"grape", price:15000}]
        }
        

    },
    async created(){
        // 서버실행
        // axios.get요청
        // productList = response.data
        const data = await axios.get("http://localhost:8080/product/list")
         console.log(data);
         
         this.productList = data.data.content;
    },
    methods: {
        login(){
            this.isLogined = true
        },
        logout(){
            this.isLogined = false
        }

    }
}
</script>