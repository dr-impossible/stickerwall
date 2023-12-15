<script lang="ts">
	import { scale } from "svelte/transition";

    interface Sticker {
        id: number,
        position: {
            x: number,
            y: number,
            rotation: number,
            scale: number
        }
        logo: {
            key: string,
            name: string
        },
        story: string,
        projectURL: string
    }

    export let sticker: Sticker

    function positionToCSS(position: number): string {
        return `${position * 100.0}%`
    }

    function scaleToCSS(scale: number): string {
        return `${scale * 100}px`
    }

    let top = positionToCSS(sticker.position.y)
    let left = positionToCSS(sticker.position.x)
    let width = scaleToCSS(sticker.position.scale)
    let height = scaleToCSS(sticker.position.scale)
</script>

<style>
    img {
        width: 100px;
        height: 100px;
        position: absolute;
    }
</style>

<img src={`logos/${sticker.logo.key}.svg`} alt={sticker.logo.name} style:top={top} style:left={left} style:width={width} style:height={height} />