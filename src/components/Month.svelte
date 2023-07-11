<script lang="ts">

    import Day from "./Day.svelte";
    import selectedMonthsStore from "../stores/SelectedMonthsStore";
    import selectedYearStore from "../stores/SelectedYearStore";

    let selectedMonths: number[]
    export let month: number
    export let daysInMonth: number

    selectedMonthsStore.subscribe(data => {
        selectedMonths = data
    })

    const months = ["January","February","March","April","May","June","July","August","September","October","November","December"]



</script>

<div style={`width: ${100/selectedMonths.length}%`}>
    <div class=" h-9 bg-slate-500 border-spacing-4 border-amber-500 b-6">
        <h1 class=" text-center leading-9">{months[month]}</h1>
    </div>
    <div>
        {#each Array(daysInMonth) as _, i}
            <Day month={month} day={i+1} />
        {/each}
            
    </div>
</div>

