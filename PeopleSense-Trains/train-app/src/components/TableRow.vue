<template>
    <tr>
        <td>{{train.id}}</td>
        <td>{{train.startStation}}</td>
        <td>{{train.endStation}}</td>
        <td>{{train.startTime}}</td>
        <td>{{train.endTime}}</td>
    </tr>
</template>


<script>

export default ({
    name: "TableRow",
    props: {
        train: Object
    }
})
</script>

<style scoped>
table, th, td {
  border:1px solid black;
}
</style>
