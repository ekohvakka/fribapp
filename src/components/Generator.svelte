<script>
    import Throw from "./Throw.svelte";
    let players = 2;

</script>

<div class="root">
    <label class="players">
        Number of players:
        <button on:click={() => players--}>-</button>
        <input type="number" class="number" value={players}>
        <button on:click={() => players++}>+</button>
    </label>
    {#each {length: players} as _, i}
        <Throw number={i + 1}/>
    {/each}
</div>

<style>
    .root {
        margin: 0.25em 0 0 0;
    }

    button {
        font-size: 14px;
        font-weight: bold;
        width: 12vw;
        margin: 0;
    }
    .players {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }
    .number {
        max-width: 30vw;
        margin: 0;
    }

    

</style>