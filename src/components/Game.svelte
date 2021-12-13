<script>
    let filter = 'all'
    export let game;
    export let index;
</script>

<style>
    .game {
        display: flex;
        flex-direction: row;
        background-color: #5EAAE7;
        align-items: center;
        margin: 0.25em 0 0.25em 0;
        border-radius: 3px;
        font-size: 16px;
        padding: 0.5em 0 0.5em 0;
    }

    input {
        flex: none;
        margin: 0 0.5em 0 1em;
    }

</style>

<div class="game">
    <input type="checkbox" id={"option".concat(index)}>
    <label for={"option".concat(index)} class="label">{game}</label>
</div>