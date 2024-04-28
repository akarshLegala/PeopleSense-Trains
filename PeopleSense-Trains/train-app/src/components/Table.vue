<template>
    <div class="table">
        <h2>{{tripType}}</h2>
        <table style="width:100%" >
            <thead>
                <tr id="head">
                    <th>Trip ID</th>
                    <th>Start Station</th>
                    <th>End Station</th>
                    <th>Start Time</th>
                    <th>End Time</th>
                    
                </tr>
            </thead> 
            <tbody>
                <tr v-for="(train, index) in trains" :key="index">
                    
                    <td :class="[train.color]">{{train.id}}</td>
                    <td :class="[train.color] "> {{train.startStation}}</td>
                    <td :class="[train.color] ">{{train.endStation}}</td>
                    <td :class="[train.color] ">{{train.startTime}}</td>
                    <td :class="[train.color] ">{{train.endTime}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>



<script>
    import TableRow from "./TableRow.vue"

    export default{
        name: "Table",
        props: {
            tripType: String,
            trains: Array
        },
        components: {
            TableRow
        },
        data() {
            return {
                color: 'grey'
            }
        },
        created() {
            for (let i = 0; i < this.trains.length; i++){
                if (i % 2 == 0) {
                    this.color = "white"
                } else {
                    this.color = "grey"
                }

                this.trains[i].color = this.color
            }
        },
        methods: {
            updateRows() {
               this.rowColor = !this.rowColor
            }
        }
    }
</script>

<style scoped>
th {
  border-bottom: 0.1em solid rgba(84, 84, 85, 0.788);
}
.table {
    padding-bottom:2em;
}

.grey {
    background-color: rgba(238, 238, 241, 0.892)
}

.white {
    background-color: rgba(251, 251, 255, 0.883)
}

td {
    padding: 0.6em;
}


</style>