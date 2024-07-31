<script>
  import TitleContainer from "./titleContainer.svelte";
  import ScrollTitle from "./scrollTitle.svelte";
</script>

<main>
  <ScrollTitle />
  <!-- <TitleContainer /> -->
</main>

<style>
  :global(html, body) {
    margin: 0;
    padding: 0;
    /* width: 100%; */
  }

  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  /* h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
    border: 1px solid black;
    display: inline-block;
  } */

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
