<script>
    import Throw from "./Throw.svelte";
    let players = 2;
</script>

<div class="root">
    <div class="players">
        <div>Number of players:</div>
        <div class="actions">
            <button on:click={() => players--}>-</button>
            <input id="number" type="number" class="number" value={players} />
            <button on:click={() => players++}>+</button>
        </div>
    </div>
    {#each { length: players } as _, i}
        <Throw number={i + 1} />
    {/each}
</div>

<style>
    .root {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 0 3vw 0 3vw;
        margin: 0;
    }

    button {
        font-size: 14px;
        font-weight: bold;
        min-width: 10vw;
        max-width: 15vw;
        margin: 0;
        background-color: #edf2f7;
        color: #718096;
        border-radius: 3px;
        text-align: center;
    }
    .players {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        min-width: 50%;
    }

    @media (max-width: 400px) {
        .players {
            max-width: 100%;
        }
    }

    .number {
        max-width: 30vw;
        margin: 0;
        text-align: center;
    }

    .actions {
        display: flex;
        flex-direction: row;
        justify-content: center;
        white-space: nowrap;
    }
</style>
