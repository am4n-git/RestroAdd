<template>
    <Header />
    <h1>Hello {{name}}</h1>
    <h3>Home Component</h3>
    <table border="">
        <tr >
            <th>id</th>
            <th>Name</th>
            <th>Address</th>
            <th>Contact</th>
            <th>Actions</th>
        </tr>
        <tr v-for="item in restaurant" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.address}}</td>
            <td>{{item.contact}}</td>
            <td><router-link :to="'/update/'+item.id">Update</router-link></td>


        </tr>
    </table>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:"Home",
    data(){
        return{
            name:'',
            restaurant:[]
        }
    },
    components:{
        Header
    },
    async mounted()
    {
            let user = localStorage.getItem('user-info');
            this.name = JSON.parse(user).name
            if(!user){
                this.$router.push({name:'Signup'})
            }
            let result = await axios.get('http://localhost:3000/restaurant')
            console.log(result)
            this.restaurant= result.data
    }
}
</script>

<style>
    td{
        width: 160px;
        height: 40px;
    }
</style>