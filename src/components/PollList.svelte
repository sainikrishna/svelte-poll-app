<script>

  import PollDetails from "./PollDetails.svelte";
    import PollStore from "../stores/PollStore";
  import { fade, scale } from "svelte/transition";
  import { flip } from "svelte/animate";
//   import { onMount, onDestroy } from "svelte";

    // let polls = [];

    // const unsb = PollStore.subscribe(data => {
    //     polls = data;
    // })

    // onMount(() => {
    //     console.log("Component Mounted");
    // });

    // onDestroy(() => {
    //     unsb();
    //     console.log("Component Destryed")
    // })

</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:scale|local animate:flip={{duration: 500}}>
            <PollDetails {poll} />
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>