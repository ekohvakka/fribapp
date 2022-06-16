<script>
    import Popup from "../common/Popup.svelte";
    import { getContext } from "svelte";

    const { open } = getContext("simple-modal");
    let reserve = ["Magician only"];
    let games = [
        "Forehand only",
        "Backhand only",
        "One disc only",
        "One disc only with swap",
        "Putter only",
        "Bag swap",
        "Bag swap, only foreign discs",
        "Random throw generator",
        "Rotating putter, mid, driver",
        "Best shot",
        "Worst shot",
    ];

    let selected = new Set();
    let teamsEnabled = false;
    let doublesEnabled = false;

    const randomizeGame = () => {
        console.log(selected);
        if (selected.size === 0) return;

        const selectedAsArray = [];
        for (const item of selected) {
            selectedAsArray.push(item);
        }
        const choice =
            selectedAsArray[Math.floor(Math.random() * selectedAsArray.length)];
        showPopup(choice);
    };

    const selectAll = () => {
        if (selected.size !== games.length) {
            for (const game of games) {
                if (!selected.has(game)) {
                    selected.add(game);
                }
            }
        } else {
            selected = new Set();
        }
        selected = selected;
    };

    const onBoxCheck = (event) => {
        if (event.target.checked) {
            selected.add(event.target.value);
        } else {
            selected.delete(event.target.value);
        }
        selected = selected;
    };

    const showPopup = (game) => {
        open(Popup, {
            game: game,
            teams: teamsEnabled,
            doubles: doublesEnabled,
        });
    };
</script>

<ol class="games-list">
    {#each games as game}
        <label class="game">
            <input
                type="checkbox"
                value={game}
                checked={selected.has(game)}
                on:change={onBoxCheck}
            />
            {game}
        </label>
    {/each}
</ol>

<div class="actions">
    <button
        class="half right"
        on:click={() => {
            doublesEnabled = !doublesEnabled;
            teamsEnabled = false;
        }}
        class:enabled={doublesEnabled}
    >
        Doubles
    </button>
    <button
        class="half left right"
        on:click={() => {
            teamsEnabled = !teamsEnabled;
            doublesEnabled = false;
        }}
        class:enabled={teamsEnabled}
    >
        Teams
    </button>
    <button class="right left" on:click={selectAll}> Select All </button>
    <button on:click={randomizeGame}> Randomize </button>
</div>

<style>
    .games-list {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 0 3vw 0 3vw;
        margin: 0;
    }
    .game {
        display: flex;
        flex-direction: row;
        background-color: #5eaae7;
        align-items: center;
        margin: 0.25em 0 0.25em 0;
        border-radius: 3px;
        font-size: 16px;
        padding: 0.5em 0 0.5em 0;
        min-width: 80vw;
    }
    .enabled {
        background-color: #5eaae7;
    }

    input {
        flex: none;
        margin: 0 0.5em 0 1em;
    }

    .actions {
        display: flex;
        justify-content: center;
    }

    button {
        padding: 0.5rem;
        margin: 0.5rem;
        border-radius: 3px;
    }
    .half {
        width: 20%;
        padding: 0 0 0 0;
    }

    .left {
        margin-left: 0;
    }
    .right {
        margin-right: 0;
    }

    button:hover {
        background-color: #5eaae7;
    }
</style>
