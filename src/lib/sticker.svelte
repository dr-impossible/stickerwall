<script lang="ts">
    interface Sticker {
        id: number,
        position: {
            x: number,
            y: number,
            rotation: number,
            scale: number
        }
        logo: {
            key: string
        },
        story: string,
        projectURL: string
    }

    export let sticker: Sticker
</script>

<style>
    img {
        width: 100px;
        height: 100px;
        position: absolute;
        top: 50%;
        left: 50%;
    }
</style>

<div>
    <img src={`logos/${sticker.logo.key}.svg`} />
</div>