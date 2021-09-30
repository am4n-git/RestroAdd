<template>
  <router-view />
</template>

<script>
// import Signup from './components/Signup.vue'
export default {
  name: 'App',

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  padding: 0;
  margin: 0;
}
    .register input, .add input{
        width: 250px;
        height: 35px;
        display: block;
        margin-bottom: 30px;
        margin-left: auto;
        margin-right: auto;
        border: 1px solid skyblue;
    }
    .register button, .add button{
        width: 150px;
        height: 35px;
        border: 1px solid skyblue;
        background-color: skyblue;
        cursor: pointer;
    }

</style>
