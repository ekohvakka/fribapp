<script>
    import Popup from "../common/Popup.svelte";
    import { getContext } from 'svelte';

  const { open } = getContext('simple-modal');
    let games = [
        { name:'Forehand only',                 id: 0},
        { name: 'Backhand only',                id: 1},
        { name: 'One disc only',                id: 2},
        { name: 'One disc only with swap',      id: 3},
        { name: 'Putter only',                  id: 4},
        { name: 'Bag swap',                     id: 5},
        { name: 'Bag swap, only foreign discs', id: 6},
        { name: 'Random throw generator',       id: 7}
    ];

    let selected = new Set();

    const randomizeGame = () => {
        console.log(selected);
        if (selected.size === 0) return;

        const selectedAsArray = [];
        for (const item of selected) {
            selectedAsArray.push(item);
        }
        const choice = selectedAsArray[Math.floor(Math.random() * selectedAsArray.length)];
        showPopup(games[choice].name);
    };
    
    const selectAll = () => {
        console.log(selected.size, games.length);
        if (selected.size !== games.length) {
            for (const game of games) {
                if (!selected.has(game)) {
                    selected.add(game.id);
                }
            }
        } else {
            selected = new Set();
        }
        selected = selected;
    };

    const onBoxCheck = event => {
        if (event.target.checked) {
            selected.add(parseInt(event.target.value));
        } else {
            selected.delete(parseInt(event.target.value));
        }
        selected = selected;
    };

    const showPopup = (game) => {
        open(Popup, { game: game})
    }
</script>

<ol class="games-list">
    {#each games as game}
        <label class="game">
            <input type="checkbox" value={game.id} checked={selected.has(game.id)} on:change={onBoxCheck}>
            {game.name}
        </label>
    {/each}
</ol>

<button on:click={randomizeGame}>
    Randomize
</button>
<button on:click={selectAll}>
    Select all
</button>

<style>
    .games-list {
        display: flex;
        flex-direction: column;
        width: 89vw;
        padding: 0 3vw 0 3vw;
        margin: 0;
    }
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