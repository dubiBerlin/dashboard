<template>
  <div>
    <EmployeesTable :employees="employees" @select-employee="setEmployee" ></EmployeesTable>
    

   <v-snackbar v-model="snackbar">
     <span>Name: {{employee.name}}</span> 
     <span style="margin-left: 20px">Title: {{employee.title}}</span> 
     <span style="margin-left: 20px">Salary: {{employee.salary}}</span> 
      <v-btn
        color="pink"
        text
        @click="snackbar = false"
      >
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>
<script>

  import employeesJson from "../data/employees.json";
  import EmployeesTable from "../components/EmployeesTable";

  export default {
    name: 'DashboardPage',
    components: {
      EmployeesTable
    },
    data () {
      return {
        employees:employeesJson,
        employee:"",
        selected:[],
        rowData:"",
        snackbar:false
      }
    },
    methods:{
      setEmployee(empl){
        this.employee = empl;
        this.snackbar = true;
      }
    }
  }
</script>
<style >

</style>