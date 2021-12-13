<script>
    export let number;
    const hand = ['FH', 'BH'];
    const stability = ['Understable', 'Straight', 'Overstable'];
    const disc = ['Putter', 'Mid', 'Fairway', 'Distance'];
</script>

<div class="card">
    <div class="grid-item">{number}.</div>
    <div class="grid-item">{hand[Math.floor(Math.random() * 2)]}</div>
    <div class="grid-item">{stability[Math.floor(Math.random() * 3)]}</div>
    <div class="grid-item">{disc[Math.floor(Math.random() * 4)]}</div>
</div>

<style>
    .card {
        margin-top: 0.5vh;
        border-radius: 4px;
        background-color: #6FF0B0;
        padding: 0.25em;
        display: grid;
        grid-template-columns: 0.25fr 1fr 1fr 1fr;
        align-items: center;
        min-height: 3vh;
    }

    .grid-item {
        background-color: #fff;
        padding: 0.25em;
        text-align: center;
    }
</style>