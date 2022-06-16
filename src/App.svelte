<script>
    import Modal from "./common/Modal.svelte";
    import { modal } from "./stores";

    import Games from "./components/Games.svelte";
    import Generator from "./components/Generator.svelte";
    export let menu = 1;
</script>

<Modal show={$modal}>
    <div class="main">
        <header>
            <ul class="menu">
                <li>
                    <a href="/" on:click|preventDefault={() => (menu = 1)}
                        >All challenges</a
                    >
                </li>
                <li>
                    <a href="/" on:click|preventDefault={() => (menu = 2)}
                        >Generator</a
                    >
                </li>
                <li>
                    <a href="/" on:click|preventDefault={() => (menu = 2)}
                        >Settings</a
                    >
                </li>
            </ul>
        </header>
        {#if menu == 1}
            <Games />
        {:else if menu == 2}
            <Generator />
        {:else}
            <h4>Page not found</h4>
        {/if}
    </div>
</Modal>

<style>
    :global(body) {
        padding: 0;
    }
    .main {
        text-align: center;
        margin: 0;
    }

    h4 {
        color: #ff3e00;
        text-transform: uppercase;
    }

    @media (min-width: 640px) {
        .main {
            max-width: none;
        }
    }
    li {
        display: inline;
    }
    a {
        color: #333333;
    }
    .menu {
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        width: 100%;
        padding: 0;
    }

    header {
        display: flex;
        justify-content: space-between;
        background-color: #edf2f7;
        align-items: center;
        color: #718096;
        padding: 0.5rem;
        border-bottom-width: 2px;
        margin-bottom: 0.25rem;
        height: 36px;
    }
</style>
