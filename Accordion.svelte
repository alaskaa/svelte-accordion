<script>
  import AccordionItem from "./AccordionItem.svelte";

  export let onlineGoodBoisAndGurls = [];

  let goodBoisAndGurls = onlineGoodBoisAndGurls.map((url, i) => {
    const boiOrGurl = Math.round(Math.random()) ? "Boi" : "Gurl";

    return {
      name: `Good ${boiOrGurl} ${i + 1}`,
      age: Math.floor(Math.random() * 20),
      cuteness: 11 + Math.floor(Math.random() * 4),
      url
    };
  });
</script>

<style>
  .accordion {
    max-width: 990px;
    margin: 50px auto;
    border: 1px solid slategray;
  }
</style>

<div class="accordion">
  {#each goodBoisAndGurls as doggo}
  <AccordionItem {...doggo} />
  {/each}
</div>