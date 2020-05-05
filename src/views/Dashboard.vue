<template>
  <div>
    <SalesGraph v-for="sale in sales" :key="`${sale.title}`" :sale="sale"></SalesGraph>
    <StatisticCard v-for="(statistic,index) in statistics" :statistic="statistic" :key="index" ></StatisticCard>
    <EmployeesTable :employees="employees" @select-employee="setEmployee" ></EmployeesTable>
    <EventTimeline  :timeline="timeline"  ></EventTimeline>

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