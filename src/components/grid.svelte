<script lang="ts">
  import { scale } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  export let row: number;
  export let col: number;

  let currentIndex = 0;

//   let startRow = 1;
//   let endRow = 1;
//   let startCol = 1;
//   let endCol = 1;

  const getStartRow = (index: number) => {
	currentIndex = index;

	return  Math.ceil(col || 1 / index || 1)
  }


  const getStartCol = (index: number) => {
	currentIndex = index;

	return  Math.ceil(col || 1 / index || 1)
  }

</script>

<div class="container" style="--row:{row};--col:{col}">
  {#each Array.from({ length: row * col }, (_, i) => i) as item}
    <div
      class={`${[100].includes(item) ? "" : "item"}`}
      style="--start-row:{getStartRow(item)};--start-col:{getStartCol(item)};--end-row:{getStartRow(item)};--end-col:{getStartCol(item)}"
      transition:scale={{
        duration: 500,
        delay: 500,
        opacity: 0.5,
        start: 0,
        easing: quintOut,
      }}
    >
      {item}
    </div>
  {/each}
</div>

<style>
  .item {
    grid-area: var(--start-row) / var(--start-col) / var(--end-row) /
      var(--end-col);
  }
  /* .item-0 {
    grid-area: 1 / 1 / 1 / 1;
  }
  .item-1 {
    grid-area: 1 / 2 / 1 / 4;
  }
  .item-2 {
    grid-area: 1 / 4 / 3 / 6;
  }
  .item-3 {
    grid-area: 2 / 1 / 4 / 4;
  }
  .item-6 {
    grid-area: 4 / 1 / 7 / 4;
  } */
  .container {
    margin: 5px;
    display: grid;
    gap: 5px;
    grid-template-rows: repeat(var(--row, 0), 1fr);
    grid-template-columns: repeat(var(--col, 0), 1fr);
    /* grid-template-areas: "header header "; */
  }
  .container div {
    display: flex;
    padding: 5px;
    justify-content: center;
    align-items: center;
    border: 1px;
    border-color: blue;
    border-style: dotted;
    border-radius: 5px;
  }
</style>
