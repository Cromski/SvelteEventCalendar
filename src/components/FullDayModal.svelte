<script lang="ts">
    import {clickOutside} from '../Extra/clickOutside.js';

    import dayModalStore from "../stores/DayModalStore";

    const handleClickOutside = () => {
        dayModalStore.set({visible: false, event: ""});
    }

    $: vis = $dayModalStore.visible

</script>

{#if vis}
<div use:clickOutside on:click_outside={handleClickOutside} class=" absolute bg-white w-[40%] h-[30%] top-32 border-b-black border-[1px] rounded">
    <h1 class="  ">{$dayModalStore.event}</h1>
    <h1 class="  ">{$dayModalStore.event}</h1>
    <h1 class="  ">{$dayModalStore.event}</h1>
</div>
{/if}
