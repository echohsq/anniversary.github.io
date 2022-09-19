<script setup>
import {ref} from 'vue';
const startDate = new Date("3/8/2022");
const now = new Date();
let howLong = ref('');
howLong.value = parseInt((now - startDate) / 86400000);
const units = ref(["Days", "Months", "Years"]);
let index = ref(0);
function switchUnit() {
    index.value = parseInt((index.value + 1) % 3);
    const year = parseInt(now.getUTCFullYear());
    const day = parseInt(now.getUTCDate());
    const month = parseInt(now.getUTCMonth());

    if (units.value[index.value] === "Days") {
        howLong.value = parseInt((now - startDate) / 86400000);
    } else if (units.value[index.value] === "Months") {
        if (month > 3 || (month == 3 && day > 8)) {

            howLong.value = parseInt((year - 2022) * 12 + month - 3);
        } else {
            howLong.value = parseInt((year - 2022) * 12 + month - 4);
        }
    } else {
        if (month > 3 || (month == 3 && day > 8))
            howLong.value = year - 2022;
    }
    
}
</script>
<template>
    
    <div class="anniversary-day">
        <h2 class="title">Anniversary Days</h2>
        <span class="days">{{howLong}}</span>
        <span class="unit" @click="switchUnit">{{units[index]}}</span>
    </div>

</template>
<style scoped>
@import url('https://fonts.font.im/css?family=Source+Sans+Pro');

.anniversary-day {
    font-family: "Concert One", cursive;
    display: block;
}
.days {
    color: #003135;
    font-size: 15rem;
    font-family: 'Source Sans Pro', sans-serif;
}

.unit {
    font-family: "Concert One", cursive;
    padding-left: 2rem;
    padding-top: 8rem;
    color: #003135;
    font-size: 2rem;
    cursor: pointer;
}

.title {
    align-items: center;
    margin-left: 22%;
    font-size: 1.5rem;
    color: black;
    opacity: 0.6;
}
</style>