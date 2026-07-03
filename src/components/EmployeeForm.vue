<template>
  <div id="employee-form">
    <form v-on:submit.prevent="handleSubmit">

      <label>Employee name</label>
      <input type="text" v-model='employee.name' 
      :class="{'has-error':submission && invalidname}" 
      @focus='clearstatus' @keypress="clearstatus"
      ref="firstinput"
       />


      <label>Employee Email </label>
      <input type="text" v-model='employee.email'
      :class="{'has-error':submission && invalidemail}" 
      @focus='clearstatus' @keypress="clearstatus" />

      <p v-if="submission && error" class="error-msg" >Please fill out all the required fields!</p>
      <p v-if="success" class="success-msg" >Employee Successfully added</p>

      <button> Add Employee </button>
    </form>
  </div>
</template>


<script>
export default {
  name:"employee-form",
  data(){
    return{
      submission:false,
      success:false,
      error:false,
      employee:{
        name:'',
        email:''
      }
    }
  },
  methods:{
    handleSubmit(){
      this.submission=true;
      this.clearstatus();
      
      if (this.invalidemail || this.invalidname){
        this.error=true;
        return;
      }

      this.$emit('add:employee',this.employee);
      this.$refs.firstinput.focus();
      this.employee = {
        name: "",
        email: ""
      }

      this.success=true
      this.error=false
      this.submission=false 

    },
    clearstatus(){
      this.success=false
      this.error=false
    }
  },
  computed:{
    invalidname(){
      return this.employee.name==='';
    },
    invalidemail(){
      return this.employee.email==='';
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

.has-error{
    border:1px solid red;
}

[class*='-msg']{
  font-weight:500;
}

.error-msg{
  color: red;
}
.success-msg{
  color: rgb(68, 187, 68);
}

</style>