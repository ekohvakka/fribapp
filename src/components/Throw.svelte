<script>
    export let number;
    const hands = ["FH", "FH", "BH", "BH", "BH", "BH", "BH", "BH", "BH", "BH"];
    const stabilities = ["Understable", "Straight", "Overstable"];
    const discs = ["Putter", "Mid", "Fairway", "Distance"];

    let hand;
    let stability;
    let disc;

    const randomize = () => {
        hand = hands[Math.floor(Math.random() * 10)];
        stability = stabilities[Math.floor(Math.random() * 3)];
        disc = discs[Math.floor(Math.random() * 4)];
        return;
    };
</script>

<div class="card" on:click={randomize}>
    {#if !hand}
        <div class="card empty">
            <div class="grid-item l">{number}.</div>
            <div class="grid-item r">Tap to generate.</div>
        </div>
    {:else}
        <div class="card populated">
            <div class="grid-item l">{number}.</div>
            <div class="grid-item">{hand || "Tap to generate"}.</div>
            <div class="grid-item">{stability || "Tap to generate"}</div>
            <div class="grid-item r">{disc || "Tap to generate"}</div>
        </div>
    {/if}
</div>

<style>
    .card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        min-width: 80vw;
        border-radius: 3px;
        max-height: 15vh;
    }

    .card.populated {
        margin-top: 0.25rem;
        background-color: #5eaae7;
        padding: 0.25em;
        display: grid;
        grid-template-columns: 0.25fr 1fr 1fr 1fr;
        align-items: center;
        border-radius: 3px;
    }

    .card.empty {
        margin-top: 0.5rem;
        background-color: #5eaae7;
        padding: 0.25em;
        display: grid;
        grid-template-columns: 0.25fr 1fr;
        align-items: center;
        border-radius: 3px;
    }

    .grid-item {
        background-color: #fff;
        padding: 0.25em;
        text-align: center;
    }

    .grid-item.l {
        border-radius: 3px 0 0 3px;
    }

    .grid-item.r {
        border-radius: 0 3px 3px 0;
    }
</style>
