<template>
  <div id="employee-table">
    <p v-if="employees.length<1" class='empty-table'>No employee</p>
    <table v-else >
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
          <th>Action</th>
        </tr>
      </thead>

      <tbody>

        <tr v-for="emp in employees" :key='emp.id'>

          <td v-if="editing===emp.id" >
            <input type='text' v-model="emp.name">
          </td>

          <td v-else >{{emp.name}}</td>
          <td>{{emp.email}}</td>
          <td> 
            <button  @click="editMode(emp)" class="edit-btn" >Edit</button> 
            <button @click="$emit('delete:employee',emp.id)" class="delete-btn" >Delete</button> 
          </td>

        </tr>

      </tbody>
    </table>
  </div>
</template>


<script>
export default {
  name:'employee-table',
  props:{
    employees:Array
  },
  data(){
    return {
      editing:null,
      emp:{
        name:'',
        email:''
      }
    }
  },
  methods:{
  editMode(emp){
    this.editing=emp.id;
  }
}
}

</script>

<style scoped>
  table{
    width:100%;
    border-collapse:collapse;
}

thead{
    background:#42b983;
    color:white;
}

th,
td{
    padding:14px;
    text-align:left;
    border-bottom:1px solid #ddd;
}

tbody tr:hover{
    background:#f8f8f8;
}

button{
    border:none;
    padding:8px 14px;
    border-radius:5px;
    cursor:pointer;
    margin :0 0.5rem 0 0;
}

.edit-btn{
    background:#ffc107;
    color:black;
}

.delete-btn{
    background:#dc3545;
    color:white;
}

 


</style>