<template>
    <form class="flex flex-col justify-center w-2/5 mx-auto mb-40 bg-gray-400 rounded-3xl h-2/4">
        <div class="flex justify-around">
            <div>
                <label for="from">First Currency</label>
                <select id="from" name="from" v-model="currencyA">
                    <option v-for="(item, index) in currencyList" :value="item" :key="index">{{ item }}</option>
                </select>
            </div>
            <div>
                <label for="to">Second Currency</label>
                <select id="to" name="to" v-model="currencyB">
                    <option v-for="(item, index) in currencyList" :value="item" :key="index">{{ item }}</option>
                </select>
            </div>
        </div>
        <input type="number" min="0" placeholder="Enter converted value . . ." class="self-start w-2/4 mx-auto placeholder-red-900 bg-gray-400 border-b-2 border-transparent border-black" />
    </form>
</template>

<script>
/* import axios from "axios"; */
export default {
    data() {
        return {
            currencyList: null,
            currencyA: "SGD",
            currencyB: "SGD",
        };
    },
    mounted() {
        fetch("https://currency-exchange.p.rapidapi.com/listquotes", {
            method: "GET",
            headers: {
                "x-rapidapi-key": "e105fdb4eemshb4de03762398cdap1458dejsn94242e37b0be",
                "x-rapidapi-host": "currency-exchange.p.rapidapi.com",
            },
        })
            .then((res) => res.json())
            .then((data) => (this.currencyList = data))
            .catch((err) => console.log(err));
    },
};
</script>

<style>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
input[type="number"] {
    -moz-appearance: textfield;
}
</style>
