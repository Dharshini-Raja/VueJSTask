<template>
    <div>
        <Forms @createEmployee="insert"/>
    </div>
</template>
<script>
import Forms from '@/components/FormData.vue';
import axios from 'axios'
export default{
    data(){
        return{
            employee:{},
        }
    },
    // props: {
    //     initialData: Object,
    //   },
    //   watch:{
    //     initialData(newData){
    //       if(newData){
    //         this.emp_name = newData.emp_name;
    //         this.salary = newData.salary;
    //         this.deptid = newData.deptid;
    //         this.edit = true;
    //       }else{
    //         this.resetform();
    //         this.edit = false;
    //       }
    //     }
    //   },
    // data(){
    //     flag: false,
    //     name: '',
    //     sal: '',
    //     depid: '',
    // },
    components:{
        Forms
    },
    methods:{
        insert(formData){
            //console.log(formData);
            //this.employee = {...formData};
            axios
    .post('http://127.0.0.1:3333/insertEmp', formData)
    .then((response) => console.log(response))

        }
    }
}
</script>