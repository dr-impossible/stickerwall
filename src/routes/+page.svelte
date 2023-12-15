<script>
    import Sticker from "$lib/sticker.svelte"
    import wall from "$lib/wall.json"
</script>

<div>
    {#each wall as sticker}
        <Sticker sticker={sticker} />
    {/each}
</div>