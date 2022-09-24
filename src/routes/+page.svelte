<script lang="ts">
  import { scale } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';

  let row = 0;
  let col = 0;
</script>

<div>
  <input type="number" bind:value={row} placeholder="row" />
  <input type="number" bind:value={col} placeholder="col" />
</div>

<div class="contrainer">
  {#each Array.from({ length: row }) as r, i}
    <div class="row">
      {i}
      {#each Array.from({ length: col }) as c}
        <div transition:scale="{{duration: 500, delay: 500, opacity: 0.5, start: 0, easing: quintOut}}" class="col" />
      {/each}
    </div>
  {/each}
</div>

<style>
  .contrainer {
    width: 100%;
  }
  .row {
    display: flex;
  }
  .col {
    margin: 10px;
    min-width: 50px;
    min-height: 50px;
    background-color: blue;
  }
</style>
