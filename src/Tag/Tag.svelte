<script lang="ts">
  export let tag: string;
  export let onClick: (e: string) => void;

  const onButtonClick = () => onClick(tag);
</script>

<style>
  span {
    margin-right: 0.5rem;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    border-style: solid;
    border-color: lightblue;
    padding-right: 0.5rem;
    padding-left: 0.5rem;
    border-width: 1px;
  }
  button {
    margin: 0;
    padding: 0;
    margin-left: 0.5rem;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    border-width: 0;
    width: 1rem;
    height: 1rem;
  }
</style>

<span>{tag}<button on:click={onButtonClick}>x</button></span>
