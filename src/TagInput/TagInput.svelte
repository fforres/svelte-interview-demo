<script lang="ts">
  import Tag from "../Tag/Tag.svelte";
  import SuggestionList from "../SuggestionList/SuggestionList.svelte";
  import colors from "../colors.json";
  let tags: string[] = [];
  let input: string = "";
  let inputElement: HTMLInputElement;

  const existsInTags = (toFind: string) => {
    return tags.some((tag) => tag.toLowerCase() === toFind.toLowerCase());
  };

  const onInput = (
    e: Event & {
      currentTarget: EventTarget & HTMLInputElement;
    }
  ) => {
    input = e.currentTarget.value.trim();
  };

  const addStringToTags = (tag) => {
    tags = [...tags, tag];
    input = "";
    inputElement.focus();
  };

  const onKeyDown = (e: KeyboardEvent) => {
    const cleanedInput = input.trim();
    if (e.key === "Enter" && cleanedInput && !existsInTags(cleanedInput)) {
      addStringToTags(cleanedInput);
    }
  };

  const removeTag = (tagName: string) => {
    tags = tags.filter((tag) => tag !== tagName);
  };

  const onSuggestionClicked = (tagName: string) => {
    addStringToTags(tagName);
  };

  $: filteredColors = input
    ? colors
        .map((color) => color.name.toLowerCase())
        .filter((colorName) => colorName.includes(input.trim().toLowerCase()))
        .filter((colorName) => !existsInTags(colorName))
    : [];
</script>

<style>
  .tag-input-wrapper {
    padding: 0.5em;
    border-style: solid;
    border-color: lightgray;
    border-width: 1px;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
  }

  input {
    padding: 0;
    margin: 0;
    outline: 0;
    border: none;
    flex: 1;
  }
</style>

<div class="tag-input-wrapper">
  {#each tags as tag}
    <Tag onClick={removeTag} {tag} />
  {/each}
  <input
    type="text"
    placeholder="add your tag"
    value={input}
    on:input={onInput}
    on:keydown={onKeyDown}
    bind:this={inputElement} />
</div>
<SuggestionList colors={filteredColors} onClick={onSuggestionClicked} />
