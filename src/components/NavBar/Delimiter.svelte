<script lang="ts">
  import { onMount } from "svelte";

  let delimiter;

  const conf = {
    height: 40,
    width: 24,
    gap: 8,
  }

  export const select = (index: number, list: HTMLElement) => {
    const li = list.querySelectorAll("li")[index];
    delimiter.style.left = `${li.offsetLeft + li.offsetWidth + conf.gap}px`;
    console.log("select", index)
  }

  onMount(() => {
    const { width, height } = conf;
    delimiter.style.width = `${width}px`;
    delimiter.style.height = `${height}px`;
    delimiter.style.top = `-${0}px`;
  })
</script>

<div class="delimiter" bind:this={delimiter}></div>

<style lang="scss">
  .delimiter {
    position: fixed;
    margin: 0;
    background-color: red;
  }
</style>

<!-- anime({
  targets: delimiter,
  translateY: 40,
  duration: 500,
  easing: 'easeInOutQuad',
}); -->