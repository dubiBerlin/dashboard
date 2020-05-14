<template>
  <div>
  <v-data-table
    v-model="selected"
    :headers="headers"
    :items="employees"
    :items-per-page="5"
    class="elevation-1"
    @click:row="rowClick"
    show-select
    :single-select="true"
  ></v-data-table>

  </div>
</template>
<script>
  export default {
    props:{
      employees:{
        type:Array,
        required:true
      }
    },
    data () {
      return {
        selected:[],
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
        this.$emit('select-employee', event)
      }
    }
  }
</script>
<style >

</style>