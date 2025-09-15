<script>
    export let colorScale;
    export let hoveredRegion;
    export let getRegionColor;
</script>

<div class="legend" on:mouseleave={() => {hoveredRegion = null;}}>
    {#each Object.keys(colorScale) as region}
        <!-- svelte-ignore a11y-mouse-events-have-key-events -->
        <p on:mouseover={() => {hoveredRegion = region;}}
            class:unhovered={hoveredRegion &&
            hoveredRegion !== region}>
            <span style="background-color: {getRegionColor(region)}"></span>
            {region}</p>
    {/each}
</div>

<style>
    .legend {
        display: flex;
        flex-direction: row;
        justify-content: center;
        flex-wrap: wrap;
        column-gap: 10px;
        row-gap: 5px;
        margin-bottom: 5px;
        user-select: none;
    }

    span {
        width: 9px;
        height: 9px;
        display: inline-block;
        border-radius: 50%;
    }

    p {
        font-size: 13px;
        color: rgba(0, 0, 0, 0.8);
        text-transform: uppercase;
        display: flex;
        align-items: center;
        column-gap: 3px;
        transition: opacity 300ms ease;
    }

    .unhovered {
        opacity: 0.3;
    }
</style>