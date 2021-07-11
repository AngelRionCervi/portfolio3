<script lang="ts">
  import { onMount } from "svelte";

  let delimiter;
  let list;
  let delimiterIndex;

  const delimiterConf = {
    height: 40,
    width: 24,
    gap: 8,
  }

  function select(index: number) {
    if (!delimiter || !list || delimiterIndex === index) return;
    delimiterIndex = index;
    const li = list.querySelectorAll('li')[index];
    delimiter.style.left = `${li.offsetLeft + li.offsetWidth + delimiterConf.gap}px`;
  }

  onMount(() => {
    select(0);
    const { width, height } = delimiterConf;
    delimiter.style.width = `${width}px`;
    delimiter.style.height = `${height}px`;
  })
</script>


<div class="delimiter" bind:this={delimiter}>

</div>

<nav class="nav-container">
  <ul class="nav-ul" bind:this={list}>
    <li>
      <a class="nav-text" href="#" on:click={() => select(0)}>home</a>
    </li>
    <li>
      <a class="nav-text" href="#" on:click={() => select(1)}>work</a>
    </li>
  </ul>
</nav>

<style lang="scss">
  @use '../theme' as *;

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

  .delimiter {
    position: fixed;
    margin:0;
    background-color: red;
    top: 0;
  }
</style>