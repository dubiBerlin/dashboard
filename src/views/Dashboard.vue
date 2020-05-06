<template>
  <v-container :fluid="true">
    <v-row >
      <v-col v-for="sale in sales" 
            :key="`${sale.title}`"  
            no-gutters
            cols="12"
            md="4"
             >
        <SalesGraph  :sale="sale"></SalesGraph>
      </v-col>
    </v-row> 
    
    <v-row >
      <v-col v-for="(statistic,index) in statistics" 
            :key="index"  
            cols="12"
            md="6"
            lg="3" >
        <StatisticCard  :statistic="statistic" ></StatisticCard>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" md="8">
        <EmployeesTable :employees="employees" @select-employee="setEmployee" ></EmployeesTable>
      </v-col>
      <v-col  cols="12" md="4">
        <EventTimeline  :timeline="timeline"  ></EventTimeline>
      </v-col>
    </v-row>
   <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp"  >
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
  </v-container>
</template>
<script>

  import employeesJson from "../data/employees.json";
  import salesJson from "../data/sales.json";
  import statisticsJson from "../data/statistics.json";
  import timelineJson from "../data/timeline.json";
  import EmployeesTable from "../components/EmployeesTable";
  import SalesGraph from "../components/SalesGraph";
  import StatisticCard from "../components/StatisticCard";
  import EventTimeline from "../components/EventTimeline";

  export default {
    name: 'DashboardPage',
    components: {
      EmployeesTable,
      SalesGraph,
      StatisticCard,
      EventTimeline
    },
    data () {
      return {
        timeline:timelineJson,
        statistics:statisticsJson,
        employees:employeesJson,
        sales:salesJson,
        employee:"",
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