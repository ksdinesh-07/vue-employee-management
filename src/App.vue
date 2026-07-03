<template>

  <div class="small-container">

  <h1>Employees</h1>
  <employee-table :employees="employees" @delete:employee="deleteEmployee" @edit:employee="edit_emp" />
  <employee-form @add:employee="addemployee"  />

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
          // }
        ]
      }
    },
    methods:{
      async addemployee(employe){

        try{

        const response= await fetch('https://jsonplaceholder.typicode.com/posts',{
          method:'POST',
          body:JSON.stringify(employe),
          headers:{'Content-type':'application/json;charset=UTF-8'}
          });

        const data=await response.json()

        // const last_id=this.employees.length>0?this.employees[this.employees.length-1].id:0
        // const id=last_id+1
        // const new_emp={...employe,id}
        this.employees=[...this.employees,data];

        }catch(err){
          console.log(err)
        }

      },
      
      async deleteEmployee(id){
        try{

          const response=await fetch('https://jsonplaceholder.typicode.com/users',{
            method:'DELETE'
          })

        this.employees=this.employees.filter((item)=>{
        return item.id != id
      })
        }catch(err){
          console.log(err)
        }
      
     },

     async edit_emp(id,updated_emp){
        
        try{
        const response=await fetch('https://jsonplaceholder.typicode.com/users/'+id,{
          method:'PUT',
          body:JSON.stringify(updated_emp),
          headers:{'Content-type':'application/json;charset=UTF-8'}
        })

        const data=await response.json();
        this.employees.map((item)=>{
          return item.id==id?data:item;
        })
        }catch(err){
          console.log(err)
        }                
      },

     async get_employees(){
      try{
        const response=await fetch('https://jsonplaceholder.typicode.com/users',{method:'GET'})
        const data=await response.json();
        this.employees=data;
      }catch(error){
        console.log(error)
      }
     }
    },
    mounted(){
      this.get_employees();
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