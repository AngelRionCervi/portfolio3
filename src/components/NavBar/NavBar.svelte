<script lang="ts">
  import Delimiter from 'components/NavBar/Delimiter.svelte';
  import { onMount } from "svelte";

  let list: HTMLElement;
  let select: (index: number, list: HTMLElement) => void;

  onMount(() => {
    select(0, list);
  })
</script>


<nav class="nav-container">
  <ul class="nav-ul" bind:this={list}>
    <li>
      <a class="nav-text" href="/#" on:click={() => select(0, list)}>home</a>
    </li>
    <li>
      <a class="nav-text" href="/#" on:click={() => select(1, list)}>work</a>
    </li>
  </ul>
</nav>
<Delimiter bind:select />

<style lang="scss">
  @use '../../theme' as *;

  .nav-container {
    margin-top: 20px;
  }

  .nav-text {
    color: get($colors, text, base);
    margin-left: 75px;
    text-decoration: none;
  }

  .nav-text:hover {
    color: get($colors, text, baseHover);
  }

  .nav-ul {
    list-style-type: none;
    display: flex;
    margin: 0;
  }
</style>