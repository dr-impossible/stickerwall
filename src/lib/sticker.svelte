<script lang="ts">
	import { scale } from "svelte/transition";

    interface Sticker {
        id: number,
        position: {
            x: number,
            y: number,
            rotate: string,
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
</script>

<style>
    div {
        width: 100px;
        height: 100px;
        position: absolute;
        padding: 5px;
        border: 1px solid rgba(0,0,0,0);
    }

    div:hover {
        border: 1px dotted black;
    }

    img {
        width: 100%;
        height: 100%;
    }
</style>

<div style:top={top} style:left={left} style:scale={sticker.position.scale} style:rotate={sticker.position.rotate}>
    <img src={`logos/${sticker.logo.key}.svg`} alt={sticker.logo.name} />
</div>