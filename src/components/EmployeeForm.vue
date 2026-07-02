<template>
  <div id="employee-form">
    <form v-on:submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input type="text" v-model='employee.name' />
      <label>Employee Email </label>
      <input type="text" v-model='employee.email' />
      <button> Add Employee </button>
    </form>
  </div>
</template>


<script>
export default {
  name:"employee-form",
  data(){
    return{
      employee:{
        name:'',
        email:''
      }
    }
  },
  methods:{
    handleSubmit(){
      console.log("clicked")
      this.$emit('add:employee',this.employee);
      this.employee = {
      name: "",
      email: ""
    };
    }
  }

}
</script>

<style scoped>
  form{
    display:flex;
    flex-direction:column;
    gap:15px;
    margin-bottom:30px;
}

label{
    font-weight:bold;
}

input{
    padding:12px;
    border:1px solid #ccc;
    border-radius:6px;
    font-size:16px;
}

input:focus{
    outline:none;
    border-color:#42b983;
}

button{
    background:#42b983;
    color:white;
    border:none;
    padding:12px;
    border-radius:6px;
    cursor:pointer;
    font-size:16px;
    transition:.3s;
}

button:hover{
    background:#2fa06d;
}
</style>