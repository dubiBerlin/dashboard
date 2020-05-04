<template>
  <div>
  <v-data-table
    v-model="selected"
    :headers="headersEmployees"
    :items="employees"
    :items-per-page="5"
    class="elevation-1"
    @click:row="rowClick"
    show-select
    :single-select="true"
  ></v-data-table>


   <v-snackbar
      v-model="snackbar"
    >
     {{rowData.name}} : {{ rowData.title}}
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

  export default {
    data () {
      return {
        selected:[],
        employees:employeesJson,
        rowData:"",
        snackbar:false,
        headers:[
          {
            text: 'Employee Id',
            align: 'start',
            sortable: true,
            value: 'id'
          },
          {
            text: 'Name',
            sortable: true,
            value: 'name'
          },
          { 
            text: 'Title',
            sortable: true,
            value: 'title' 
          },
          { 
            
            text: 'Salary',
            sortable: true,
            value: 'salary' 
          }
        ]
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