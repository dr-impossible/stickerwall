<script>
    import { Switch } from "@svelteuidev/core"

    import Sticker from "$lib/sticker.svelte"
    import {title, wall} from "$lib/wall.json"
</script>

<style>
    header {
        height: 30px;
        top: 0px;
        left: 0px;
        right: 0px;
        background-color: rgb(48, 95, 40);
        padding: 5px;
        margin: 0px;

        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;

    }

    .title {
        color: white;
    }
</style>

<header>
    <div class="title">{title}</div>
    <div class="edit-switch">
        <Switch size="lg" offLabel="view" onLabel="edit" />
    </div>
</header>

<div>
    {#each wall as sticker}
        <Sticker {sticker} />
    {/each}
</div>