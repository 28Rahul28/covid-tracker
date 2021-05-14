<template>
    <div class=" text-center text-2xl m-10 pl-10">
    <div class="flex flex-col bg-green-700">
        <div>New Confirmed Cases:{{data.NewConfirmed}}</div>
        <div>Total Confirmed Cases:{{data.TotalConfirmed}}</div>


    </div>
    <div class="flex flex-col bg-pink-300">
       <div> New Deaths:{{data.NewDeaths}}</div>
        <div>Total Deaths:{{data.TotalDeaths}}</div>
    </div>
    </div>
</template>

<script>
export default {
    name:"Databoxes",
    props:['data']
}
</script>