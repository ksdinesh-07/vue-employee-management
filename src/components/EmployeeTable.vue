<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>

      <tbody>

        <tr v-for="emp in employees" :key='emp.id'>
          <td>{{emp.name}}</td>
          <td>{{emp.email}}</td>
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