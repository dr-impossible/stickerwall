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

<div>
    {sticker.logo.key}
</div>