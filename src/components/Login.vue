<template>
    <form @submit.prevent="login">
    <input type="text" v-model="username" placeholder="Enter Username" required>
    <br><br>
    <input type="password" v-model="password" placeholder="Enter password" required>
    <br><br>
    <button type="submit">Login</button>
    </form>
</template>

<script>
    export default{
        data(){
            return{
            username:null,
            password: null,
            }
        },
        methods:{
            login(){
               // console.log(this.username)
                localStorage.setItem('username', this.username);
                //const username = localStorage.getItem('username');
                this.$emit('changeFlag', true)
                this.resetform();
            },
            resetform(){
                  this.username= "";
                  this.password= "";
  
  
          },
        }    }
</script>
<style>

#RouterLink{
    border: 3px solid rgb(0, 0, 0);
    border-radius: 20px;
    color: slateblue;
    background-color: black;
}
body {
  width: 100%;
  max-width: 68rem;
  margin: 0 auto;
  font: 1.6rem/1.25 "Helvetica Neue", Helvetica, Arial, sans-serif;
  background-color: rgb(54, 52, 51);
  color: #4d4d4d;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  padding-left: 150px;
}
button{
  border-radius: 30%;
  height: 50px;
  width: 150px;
  background-color: slateblue;
}
h2{
    color:aliceblue;
    font-size: 40px;
    padding-right: 100%;
    width: 1000px;
}
table {
    border: solid 4px #000000;
    border-collapse: collapse;
    border-spacing: 0;
    font: normal 13px Arial, sans-serif;
    width: 100%;
    
}
#table{
    padding-right: 25%;

}
thead th {
    background-color: #476060;
    border: solid 4px #000000;
    color: #ffffff;
    padding: 30px;
    text-align: left;
    font-size: 20px;
    text-shadow: 1px 1px 1px #fff;
}
tbody td {
    border: solid 4px #000000;
    color: #f9f9f9;
    padding: 10px;
    font-size: 20px;
}
body {
  width: 100%;
  max-width: 68rem;
  margin: 0 auto;
  font: 1.6rem/1.25 "Helvetica Neue", Helvetica, Arial, sans-serif;
  background-color: rgb(54, 52, 51);
  color: #4d4d4d;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  padding-left: 150px;
}
label{
    color: black;
}
input{
  font-family: inherit;
  font-size: 100%;
  line-height: 1.15;
  margin: 0;
  overflow: visible;
}
input[type="text"] {
  border-radius: 0;
}

form{
  border: 4px solid black;
  background-color: rgb(85, 83, 83);
  align-items: center;
  padding-left: 25%;
  padding-top: 10%;
  width: 800px;
}
#submit{
  padding-left: 20%;
  padding-bottom: 20%;
  border-radius: 50%;
  height: 5px;
}
button{
  border-radius: 30%;
  height: 50px;
  width: 150px;
  background-color: slateblue;
}
h2{
  color:rgb(0, 0, 0);
  padding-right: 40%;
  text-align: center;
}
@media screen and (min-width: 620px) {
  body {
    font-size: 1.9rem;
    line-height: 1.31579;
  }
}
</style>