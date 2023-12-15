<script>
    import { Switch } from "@svelteuidev/core"

    import Sticker from "$lib/sticker.svelte"
    import {title, wall} from "$lib/wall.json"
</script>

<div class="header">
    <div class="title">{title}</div>
    <Switch size="lg" offLabel="view" onLabel="edit" />
</div>

<div>
    {#each wall as sticker}
        <Sticker {sticker} />
    {/each}
</div>