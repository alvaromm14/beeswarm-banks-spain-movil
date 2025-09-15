<script>
    export let yScale;
    export let width;

    $: ticks = [2009, 2015, 2020, 2025]
</script>

<g>
  {#each ticks as tick}
    <g class="tick" transform="translate(0, {yScale(tick)})">
      <text 
        x="-6"                
        y="0" 
        text-anchor="end"   
        dominant-baseline="middle"
      >
        {tick}
      </text>
      <line 
        x1="0" 
        x2={width}           
        y1="0" 
        y2="0" 
        stroke="hsla(215, 15%, 91%, 1)" 
      />
    </g>
  {/each}
</g>