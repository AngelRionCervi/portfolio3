<script lang="ts">
  import { onMount } from "svelte";
  import anime from "animejs";

  let delimiter: HTMLElement;
  let delimiterIndex: number;
  let firstLoad = true;

  const conf = {
    height: 40,
    width: 24,
    gap: 10,
    duration: 350,
    easing: "linear",
  };

  const animate = (down: boolean, complete?: Function) => {
    const { height, duration, easing } = conf;
    anime({
      targets: delimiter,
      translateY: down ? height : -height,
      duration: duration,
      easing: easing,
      complete,
    });
  };

  export const select = (index: number, list: HTMLElement) => {
    if (delimiterIndex === index) return;
    delimiterIndex = index;
    const li = list.querySelectorAll("li")[index];
    if (!firstLoad) {
      animate(false, () => {
        delimiter.style.left = `${li.offsetLeft + li.offsetWidth + conf.gap}px`;
        animate(true);
      });
    } else {
      delimiter.style.left = `${li.offsetLeft + li.offsetWidth + conf.gap}px`;
      animate(true);
    }

    firstLoad = false;
  };

  onMount(() => {
    const { width, height } = conf;
    delimiter.style.width = `${width}px`;
    delimiter.style.height = `${height}px`;
    delimiter.style.top = `-${height}px`;
  });
</script>

<div class="delimiter" bind:this={delimiter} />

<style lang="scss">
  @use '../../theme' as *;

  .delimiter {
    position: fixed;
    margin: 0;
    background-color: get($colors, main);
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  }
</style>
