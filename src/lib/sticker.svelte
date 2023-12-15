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
    export let editable: boolean

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
    
    .bounding-box {
        --ui-icon-size: 20px;
        position: absolute;
        padding: 5px;
        border: 1px solid rgba(0,0,0,0);
    }
    
    .editable.bounding-box:hover {
        border: 1px dotted black;
    }
    
    .editable.bounding-box:hover .ui-handle {
        visibility: visible;
    }

    img.sticker {
        width: 100px;
        height: 100px;
        width: 100%;
        height: 100%;
    }

    img.ui-handle {
        width: var(--ui-icon-size);
        height: var(--ui-icon-size);
        position: absolute;
        visibility: hidden;
    }

    img.ui-rotate {
        top: calc(-1 * var(--ui-icon-size));
        right: calc(-1 * var(--ui-icon-size));
    }

    img.ui-resize {
        bottom: calc(-1 * var(--ui-icon-size));
        right: calc(-1 * var(--ui-icon-size));
    }
</style>

<div class="bounding-box" class:editable={editable} style:top={top} style:left={left} >
    <img class="sticker" src={`logos/${sticker.logo.key}.svg`} alt={sticker.logo.name} style:width={width} style:height={height} style:rotate={sticker.position.rotate} />
    <img class="ui-handle ui-rotate" src={`icons/rotate.svg`} alt="rotate" />
    <img class="ui-handle ui-resize" src={`icons/square.svg`} alt="resize" />
</div>