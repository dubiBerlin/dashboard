<template>
  <div>
    <EmployeesTable :employees="employees" ></EmployeesTable>
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
        selected:[],
        rowData:"",
        snackbar:false
      }
    },
    methods:{
      rowClick(event){
        this.rowData = event;
        console.log("rowData: ",this.rowData);
        console.log("SELECTED: ",this.selected)
        this.snackbar = true;
      }
    }
  }
</script>
<style >

</style>