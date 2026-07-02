<template>

  <div class="small-container">

  <h1>Employees</h1>
  <employee-table :employees="employees" />
  <employee-form @add:employee="addemployee" />

  </div>
  

</template>

<script >

  import EmployeeTable from "./components/EmployeeTable.vue";
  import EmployeeForm from "./components/EmployeeForm.vue"

  export default{
    name:'App',
    components:{
      EmployeeTable,
      EmployeeForm
    },
    data(){
      return {
        employees:[
          // {
          //   id:1,
          //   name:"alice",
          //   email:"alice90@gamil.com"
          // },  
          
          // {
          //   id:2,
          //   name:"bob",
          //   email:"bob340@gamil.com"
          // },
          
          // {
          //   id:3,
          //   name:"charlie",
          //   email:"charle40@gamil.com"
          // },          

        ]
      }
    },
    methods:{
      addemployee(employe){
        this.employees=[...this.employees,employe];
      }
    }
  }
</script>


<style scoped>

button{
  background: #009435;
  border: 1px solid #009435;
}

.small-container{
    width:90%;
    max-width:800px;
    margin:40px auto;
    background:#fff;
    padding:30px;
    border-radius:12px;
    box-shadow:0 5px 15px rgba(0,0,0,.1);
}

h1{
    text-align:center;
    margin-bottom:25px;
    color:#2c3e50;
}
  


</style>