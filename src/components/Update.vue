<template>
    <Header />
    <h1>Update</h1>
        <form class="add">

        <input type="text" placeholder="Restro Name" v-model="restaurant.name" name="name">
        <input type="text" placeholder="Address" v-model="restaurant.address" name="address">
        <input type="tel" placeholder="Contact" v-model="restaurant.contact" name="contact">
        <button type="button" v-on:click="updateRestro">Update Restro</button>

    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:'Update',
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
    async mounted(){
                    let user = localStorage.getItem('user-info');
            // this.name = JSON.parse(user).name
            if(!user){
                this.$router.push({name:'Signup'})
            }
        const result = await axios.get('http://localhost:3000/restaurant/'+this.$route.params.id)
        // console.log(result)
        this.restaurant= result.data
    },
    methods:{
         async updateRestro(){
            const result = await axios.put('http://localhost:3000/restaurant/'+this.$route.params.id,{
                name:this.restaurant.name,
                address:this.restaurant.address,
                contact:this.restaurant.contact
            })
            if(result.status==200){
                this.$router.push({name:'Home'})
            }
            
        }
    }
}
</script>