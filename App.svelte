<script>
  import Accordion from "./Accordion.svelte";

  async function getGoodDoggos(num) {
    const nDoggos = num ? num : Math.floor(Math.random() * 10);

    let res = await fetch(`https://dog.ceo/api/breeds/image/random/${nDoggos}`);

    if (res.ok) {
      const JSON = await res.json();
      return JSON.message;
    } else {
      return [];
    }
  }

  let goodBoisAndGurls = getGoodDoggos(5);
  console.log(goodBoisAndGurls);
</script>

<style>
  main {
    font-family: sans-serif;
    margin: 50px 0;
  }

  h1,
  h2 {
    text-align: center;
  }
</style>

<main>
	<h1>Hello Good Bois & Gurls 👋</h1>
  {#await goodBoisAndGurls}
  <p>... loading doggos</p>
  {:then doggos}
  <Accordion onlineGoodBoisAndGurls={doggos}/>
  {/await}
  <h2>They're good dogs, Brent!</h2>
</main>