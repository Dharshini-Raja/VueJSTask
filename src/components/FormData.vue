<template> 
    <form @submit.prevent="insert"> 
      <h2>Employees Details Form</h2><br>
    <input type="text" v-model="name"  placeholder="Enter employee name"><br>
    <input type="text" v-model="sal"  placeholder="Enter salary"><br>
    <input type="text" v-model="deptid" placeholder="Enter dept id"><br>
<br><br>
<div id="submit">
    <button type="submit" >  Create  </button>
</div>
    </form>
</template>
<script>


export default { 

    data () {
        return{
            name: '',
            sal: '',
            deptid: '',
            //flag: false,

        };
    },
    methods:{
    insert() {
        const formData = {
              emp_name: this.name,
              salary: this.sal,
              dept_id: this.deptid
            };
    //    console.log(formData);
     this.$emit('createEmployee',formData);
     
  },
}
}
</script>



<style>

</style>