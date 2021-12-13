<script>
    import Modal from "./common/Modal.svelte";
    import { modal } from "./stores";

    import Games from "./components/Games.svelte";
    import Generator from "./components/Generator.svelte";
    export let menu = 1;
</script>

<Modal show={$modal}>
    <div class="main">
        <div class="header">
            <ul class="menu">
                <li><a href="/" on:click|preventDefault={() => (menu = 2)}>All challenges</a></li>
                <li><a href="/" on:click|preventDefault={() => (menu = 2)}>Generator</a></li>
                <li><a href="/" on:click|preventDefault={() => (menu = 2)}>Settings</a></li>
            </ul>
        </div>
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
    
    .header {
        background-color: #49C0EB;
        border-radius: 4px;
        width: 96vw;
        height: 6vh;
        text-align: center;
        display: flex;
        flex-direction: row;
        align-items: center;
    }
</style>