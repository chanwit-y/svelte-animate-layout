<script lang="ts">
  import Grid from "../components/grid.svelte";

  let row = 0;
  let col = 0;
</script>

<div>
  <input type="number" bind:value={row} placeholder="row" />
  <input type="number" bind:value={col} placeholder="col" />
</div>
<Grid row={row} col={col} />

<!-- <script lang="ts">
  import { scale } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  let row = 0;
  let col = 0;
  let selected: string[] = [];
</script>

<div>
  <input type="number" bind:value={row} placeholder="row" />
  <input type="number" bind:value={col} placeholder="col" />
</div>

<div class="contrainer">
  {#each Array.from({ length: row }) as r, ir}
    <div class="row">
      {#each Array.from({ length: col }) as c, ic}
        <div
          class="col"
          transition:scale={{
            duration: 500,
            delay: 500,
            opacity: 0.5,
            start: 0,
            easing: quintOut,
          }}
	  on:click={() => {
		console.log(row)
		console.log(col)
		selected = [...selected, `${ir},${ic}`]
	  }}
        />
      {/each}
    </div>
  {/each}
</div>
{JSON.stringify(selected)}

<style>
  .contrainer {
    width: 100%;
  }
  .row {
    display: flex;
  }
  .col {
    margin: 5px;
    min-width: 50px;
    min-height: 50px;
    opacity: 0.5;
    border: 1px
    border-color: blue;
    border-style: dotted;
    border-radius: 5px;
    cursor: pointer;
  }
</style> -->
