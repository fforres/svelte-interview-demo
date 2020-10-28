<script lang="ts">
  export let colors: string[];
  export let onClick: (color: string) => void;
</script>

<style>
  li {
    display: flex;
    cursor: pointer;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
    padding-top: 0.5rem;
  }
  div {
    max-height: 250px;
    overflow-y: scroll;
  }
</style>

<div>
  {#each colors as color}
    <li on:click={() => onClick(color)}>{color}</li>
  {/each}
</div>
