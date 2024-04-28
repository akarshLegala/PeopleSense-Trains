<template>
    <h2>Train Companies</h2>
    <form @submit="onSubmit" class="add-form">
        <div  v-for="(company, index) in trainCompanies" :key="index" class="form-control">
            <input class="rbtn" :id="index" :value="index" type="radio" v-model="trainID" name="bts"/>
            <label class="btn-label" :for="index">{{company}}</label>
            
        </div>
        <input class="button" id="btn" @onclick="clicked()" type="submit" value="Submit Train" >
    </form>
</template>

<script>
    export default {
        name: "TrainSelection",
        data () {
            return {
                trainID: null,
            }
        },
        props: {
            trainCompanies: Array
        },
        methods: {
            onSubmit(e) {
                e.preventDefault();
                if (this.trainID != null) {
                    this.$emit('train-select', this.trainID);

                    let btn = document.getElementById(`${this.trainID}`);
                    btn.checked=false;
                    this.trainID = null;

                } else {
                    alert("Please select a train")
                }
            }
        }

    }
</script>

<style scoped>

    .rbtn {
        width: 1.5em;
        height: 1.5em;
        padding: 2em;
        margin: 3em;
    }

    .btn-label {
        font-size: 1.5em;
        padding: 1em;
    }

    /* #btn {
        padding:1em;
        border-radius: 1em;
        margin:1em;
    }

    #btn:hover {
        background-color: aquamarine;
        transition-property: background-color;
        transition-duration: 0.7s;
    } */
</style>