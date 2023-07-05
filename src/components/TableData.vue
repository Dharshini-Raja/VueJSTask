<template> 
<div id="dropdown">
	<select v-model="selectedDept" @click="fetchDept">
      
      <option v-for="(item,index) in depts" :key="index" :value="item.id">{{ item.dept_name }}</option>
      <option value="" disabled selected>Select an option</option>
      <option value="all">all</option>
      
    </select>
</div>
<div>
  <input type="text" v-model="search" placeholder="Search" @input="searchData"/>
  <button @click="searchData">Search</button>
</div>
<div id="msg">{{ result }}</div>
<div id="body" v-if="this.flag">
    <h2> Employee Particulars        
    </h2><br>
        <div id="table">
            <table>
                <thead>
                    <tr>
                        <th v-for="(key, index) in headers" :key="index" >{{ key }}</th>
                        
                        <th>Update</th>
                        <th>Delete</th>
                    </tr>
                </thead>
                <tbody>
                    <tr  v-for ="(item,index) in arr" :key="index">
                        <td>{{  item.id }}</td>
                        <td>{{  item.emp_name }}</td>
                        <td>{{ item.dept_id }}</td>
                        <td>{{ item.salary }}</td>
                        <td><button @click="editItem(item.id)">Edit</button></td>
                        <td><button @click="deleteItem(item.id)">Delete</button></td>
                      
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
<script>
import axios from 'axios'


export default { 
    name: 'Tables',
    mounted() {
    //this.select();
},
    data () {
        return{
            
            arr: [],
            flag: '',
            baseURL: import.meta.env.VITE_BASE_URL,
            selectedDept: '',
            depts: null,
            search: null,
            headers: [],
            result: null,
        };
    },
    created (){
    this.emitter.on('reload', this.select) ;
    //console.log('created hook');
    this.select()
  },
  // beforeUnmount() {
  //   // Clean up the event listener
  //   //console.log('beforeUnmount hook');
  //   this.emitter.off('reload', this.select);
  // },
 
  // beforeCreate() {
  //   console.log('beforeCreate hook');
  // },
  // beforeMount() {
  //   console.log('beforeMount hook');
  // },
  // mounted() {
  //   console.log('mounted hook');
  // },
  // beforeUpdate() {
  //   console.log('beforeUpdate hook');
  // },
  // updated() {
  //   console.log('updated hook');
  // },
  // unmounted() {
  //   console.log('unmounted hook');
  //   location.reload();
  // },


    methods:{
      searchData(){
          console.log(this.search)
          // Get the input element and table
          
          axios.get(`${this.baseURL}searchAll/?search=${this.search}`)
         //axios.get(`http://127.0.0.1:3333/searchAll/?search=2023`)
    .then((response) => {
        this.arr=response.data;
        console.log(this.arr);
        console.log(this.arr.length)
      if (this.arr.length == 0 )  {this.result = "No Results"}
      else{ this.result = ""}
      }).catch((err) => {
        console.log(err);
      })  
      

      },
      fetchDept(value) {
       
			//this.activeInstrument = instrument;
      axios.get(`${this.baseURL}selectAllDept`)
    .then((response) => {
        this.depts=response.data;
        console.log(this.depts);
      }).catch((err) => {
        console.log(err);
      })
      console.log( value,"val");

      if(this.selectedDept=='all'){
         this.select();}
      
    else if(this.selectedDept!='all'){
console.log(this.selectedDept)
     axios.get(`${this.baseURL}joinById/${this.selectedDept}`)
    .then((response) => {
        this.arr=response.data;
        console.log(this.arr);
      }).catch((err) => {
        console.log(err);
      })
    // }else{
    //   this.select();
     }
    
		},
  deleteItem(item){
    let result = confirm("Do you want to delete the record?");
        if(result){
        axios.get(`${this.baseURL}deleteEmp/${item}`)
    .then((response) => {
        console.log(response);
       this.select();
      })
    }else{
        alert("Not Deleted!");
    }
  },
  editItem(item){
    this.emitter.emit('getId', {'eventContent': item})
  },
  select() {
        axios.get(`${this.baseURL}selectAllEmp`)
    .then((response) => {
        this.arr=response.data;
        console.log(this.arr);
        this.headers =  Object.keys(this.arr[0]).slice(0, 4);
     console.log(this.headers)
        this.flag = true
      }).catch((err) => {
        console.log(err);
        this.flag = false;
      })
     
    },
  
},
}
</script>



<style>
#msg{
color:white;
}
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