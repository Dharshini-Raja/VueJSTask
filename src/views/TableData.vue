<script>
import axios from 'axios'
//import Forms from '@/components/FormData.vue'
export default { 
    data () {
        return{
        arr: [],
        // editItemData: null,
        // editIndex: null,
        };
    },
    mounted() {
        axios.get('http://127.0.0.1:3333/selectAllEmp')
    .then((response) => {
        this.arr=response.data;
       // console.log(this.arr);
      })

  },
  methods:{
   
    editItem(item,index){
        this.editItemData = {...item};
        this.editIndex = index;
       // console.log(this.editItemData);
    }
  }
}
</script>

<template> 
<!-- <Forms :initialData="editItemData" /> -->
    <div id="body">
    <h2> Employee Particulars        <RouterLink to="/form" id="RouterLink"> Create </RouterLink></h2><br>
        <div id="table">
            <table>
                <thead>
                    <tr>
                        <th >ID</th>
                        <th>Name</th>
                        <th>Salary</th>
                        <th>Dept ID</th>
                        <th>Update</th>
                    </tr>
                </thead>
                <tbody>
                    <tr  v-for ="(item,index) in arr" :key="index">
                        <td>{{ item.id }}</td>
                        <td>{{ item.emp_name }}</td>
                        <td>{{ item.salary }}</td>
                        <td>{{ item.dept_id }}</td>
                        <td><button @click="editItem(item,index)">Edit</button></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<style>
#RouterLink{
    border: 2px solid black;
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
    padding-left: 15%;
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