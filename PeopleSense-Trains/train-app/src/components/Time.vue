<template>
    <h2>{{time}}</h2>
    <p>(All Times Given in PST)</p>
</template>

<script>
    export default ({
        // eslint-disable-next-line
        name: "Time",
        data() {
            return{ 
                time: ""
            }
        },
        mounted: function () {
            // Updates time dynamically
            setInterval(function () {
                this.getTime();
                try {
                this.$emit('refresh');
                } catch(e) {

                }
            }.bind(this), 1000)
        },
        methods: {
            getTime() {
                // Gets all needed components to make the date
                let date = new Date();
                let year = date.getFullYear()
                let day = date.getDate()
                let month = date.getMonth()
                let hours = date.getHours();
                let minutes = date.getMinutes();
                
                // Abreviation is set to AM by default
                let abrev = "AM";
                // Changes to PM if hours are greater than or equal to 12
                if (hours >= 12) {
                    hours = hours % 12;
                    abrev = "PM"
                }

                if (hours == 0) {
                    hours = 12
                }



                // Adds a 0 minutes is less than 10
                // Ex: 
                // Before: 8:5 PM
                // After: 8:05 PM
                if (minutes < 10) {
                    this.time =  + (month + 1 )+ "/" + day +"/"+ year + " " + hours + ":0" + minutes+ " " + abrev;
                } else {
                    this.time =  + (month + 1 ) + "/" + day +"/"+ year + " " + hours + ":" + minutes+ " " + abrev;
                }
                
            }
        },
        emits: ['refresh']
    })
</script>