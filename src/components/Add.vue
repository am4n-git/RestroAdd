<template>
    <Header />
    <h1>Add</h1>
    <form class="add">
        <input type="text" placeholder="Restro Name" v-model="restaurant.name" name="name">
        <input type="text" placeholder="Address" v-model="restaurant.address" name="address">
        <input type="tel" placeholder="Contact" v-model="restaurant.contact" name="contact">
        <button type="button" v-on:click="addRestro">Add Restro</button>

    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:'Add',
    components:{
        Header
    },
    data(){
        return{
            restaurant:{
                name:'',
                address:'',
                contact:''
            }
        }
    },
    methods:{
        async addRestro(){
            const result = await axios.post('http://localhost:3000/restaurant',{    
                name:this.restaurant.name,
                address:this.restaurant.address,
                contact:this.restaurant.contact

            });
            if(result.status==201){
                this.$router.push({name:'Home'})
            }

        }
    },
    async mounted()
    {
            let user = localStorage.getItem('user-info');
            // this.name = JSON.parse(user).name
            if(!user){
                this.$router.push({name:'Signup'})
            }
    }
}
</script>
