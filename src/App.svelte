<script lang="ts">
  import NavBar from "components/NavBar.svelte";
</script>

<main class="main">
  <NavBar />
</main>

<style lang="scss">
  @use 'theme' as *;
  @import url('https://fonts.googleapis.com/css2?family=Karla:wght@200&display=swap');

  :global(body) {
    font-family: 'Karla', sans-serif;
    background-color: get($colors, background);
    margin: 0;
    padding: 0;
  }
</style>
