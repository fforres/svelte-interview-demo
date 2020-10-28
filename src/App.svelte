<script lang="ts">
  import TagInput from "./TagInput/TagInput.svelte";
</script>

<style>
  main {
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <TagInput />
</main>
