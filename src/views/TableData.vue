<script>
import axios from 'axios'
import Tables from '@/components/TableData.vue'
import Forms from '@/components/FormData.vue'
export default { 
    data () {
      return {

      }
    },
  components:{
    Forms,
    Tables,

  },

 
}
</script>

<template> 
<div>
    <Forms  />
    </div>
    <br><br>
    <div>
    <Tables />
</div>
</template>

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
</style>