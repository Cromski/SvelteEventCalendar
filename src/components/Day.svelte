<script lang="ts">
    
    import selectedYearStore from "../stores/SelectedYearStore";
    import monthsStore from "../stores/MonthsStore";

    export let month: number
    export let day: number

    $: today = new Date(`${$selectedYearStore} ${$monthsStore[month]} ${day}`).toLocaleDateString("da-dk", {weekday: "short"})

    const getWeekNumber = () => {
        var date = new Date(`${$selectedYearStore} ${$monthsStore[month]} ${day}`);
        date.setHours(0,0,0,0)
        date.setDate(date.getDate() +3 - (date.getDay() +6) % 7)
        var week1 = new Date(date.getFullYear(), 0, 4)
        return 1 + Math.round(((date.getTime() - week1.getTime()) / 86400000 - 3 + (week1.getDay() +6 ) % 7) / 7);
    }

    const convertToShorterWeekday = (weekday: string) => {
        if (weekday === "man.") return "Ma"
        else if (weekday === "tirs.") return "Ti"
        else if (weekday === "ons.") return "On"
        else if (weekday === "tors.") return "To"
        else if (weekday === "fre.") return "Fr"
        else if (weekday === "lør.") return "Lø"
        else return "Sø"
    }

</script>


<div class={today == "lør." ? ` bg-slate-200 flex w-full h-6` : today == "søn." ? ` bg-slate-400 flex w-full h-6` : ` bg-white flex h-6 w-full`}>
    <div class=" min-w-[44px] max-w-[44px] bg-slate-800 text-gray-300 text-xs leading-6">
        <h1 class=" ml-1 inline-block">{day}.</h1>
        <h1 class=" mr-1 inline-block float-right">{convertToShorterWeekday(today)}</h1>
    </div> 
    <h1 class=" ml-1 mr-auto truncate ">co co co co c</h1>
    {#if today == "man."}
        <h1 class=" mr-1 w-4 text-xs">{getWeekNumber()}</h1>
    {/if}
    
</div>