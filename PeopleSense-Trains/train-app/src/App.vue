<template>
  <Header/>
  
  <h1 v-show="!trainSelection">Please Choose Your Transportation Service</h1>
  <h1>Billy Branch go Brr</h1>
  <h3>helo susy boki</h3>
  <h1 v-show="trainSelection">{{trainCompany}} Train Schedules</h1>
  <Time @refresh="refresh"/>
  <div v-show="!trainSelection">
    <TrainSelection @train-select="trainSelected" :trainCompanies="trainCompanies"/>
  </div>
  

  <div v-show="trainSelection" class="content">
    <Table tripType="Completed Trips" :trains = "completedTrips"/>
    <Table tripType="Ongoing Trips" :trains = "ongoingTrips"/>
    <Table tripType="Upcoming Trips" :trains = "upcomingTrips"/>
  </div>

  <button class="button" v-show="trainSelection" @click="goBack" >Go Back</button>

  <Footer />


</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from "./components/Header.vue"
import Time from "./components/Time.vue"
import Table from "./components/Table.vue"
import Footer from "./components/Footer.vue"
import TrainSelection from "./components/TrainSelection.vue"

export default {
  name: 'App',
  components: {
    Header,
    Time,
    Table,
    Footer,
    TrainSelection
  },
  data() {
    return {
      trainCompany: "",
      trainCompanies: [],
      trainSelection: false,
      completedTrips: [],
      ongoingTrips: [],
      upcomingTrips: []
    }
  },
  created() {
    this.completedTrips = [
      {
        id: "Train 01",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      }, 
       {
        id: "Train 04",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
       {
        id: "Train 05",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 14",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
    ]

    this.ongoingTrips = [
      {
        id: "Train 02",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      }, {
        id: "Train 06",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 09",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 13",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },

    ]

    this.upcomingTrips = [
      {
        id: "Train 03",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""
      },
      {
        id: "Train 07",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 08",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 11",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
      {
        id: "Train 15",
        startStation: "Sacaremento",
        endStation: "Los Angeles",
        startTime: "1:00 PM",
        endTime: "8:00 PM",
        color: ""

      },
    ]

    this.trainCompanies = ["ACE", "CC", "SJJ"]
  },
  methods: {
    refresh() {
      // console.log("sus")
    },

    trainSelected(id) {
      this.trainCompany = this.trainCompanies[id];
      this.trainSelection = true;
    },

    goBack() {
      this.trainSelection = false;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

.button {
  padding:1em;
  border-radius: 1em;
  margin:1em;
}

.button:hover {
  background-color: aquamarine;
  transition-property: background-color;
  transition-duration: 0.8s;
}
</style>
