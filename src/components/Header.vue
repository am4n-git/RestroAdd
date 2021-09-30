<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Restro</router-link>
        <!-- <router-link to="/update">Update Restro</router-link> -->
        <a v-on:click="logout">Logout</a>
        <div class="welcome">Welcome {{name}}</div>
    </div>
</template>

<script>
export default {
    name:'Header',
    data(){
        return{
            name:''
        }
    },
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name:'Login'})
        }
    },
    mounted(){
            let user = localStorage.getItem('user-info');
            this.name = (JSON.parse(user).name).toUpperCase();
    }
}
</script>

<style>
    .nav{
        background-color: #2b2b2b;
        overflow: hidden;
    }
    .nav a{
         color: white;
        text-decoration: none;
        cursor: pointer;
        float: left;
        padding: 10px 14px;
        font-size: 20px;
        margin: 5px 10px;
        transition: .3s ease-in-out;
        border-radius: 6px;
    }
    .nav a:hover{
        color: black;
        background-color: rgb(212, 209, 209);
    }
    .welcome{
        color: rgb(0, 255, 255);
        font-size: small;
        text-align: center;
        float: right;
        margin-top: 15px;
        margin-right: 10px;
    }
</style>
