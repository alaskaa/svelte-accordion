<script>
  export let name;
  export let age;
  export let cuteness;
  export let url;

  let isOpen = false;

  const handleClick = () => {
    isOpen = !isOpen;
  };
</script>

<style>
  .accordion_item {
    background-color: cadetblue;
    border-top: 1px solid slategray;
    width: 100%;
  }

  .accordion_item:first-of-type {
    border-top: none;
  }

  .accordion_item--header {
    padding: 24px;
    text-align: left;
    min-height: 40px;
    max-height: 120px;
    display: flex;
    align-items: center;
    color: #fff;
    font-weight: 900;
    cursor: pointer;
  }

  .accordion_item--header:hover {
    transform: scale(1.05);
    transform-origin: left;
  }

  .accordion_item--data {
    /* display: none; */
    padding: 24px;
    background-color: salmon;
  }

  .accordion_item--data img {
    height: 250px;
    padding: 10px;
    text-align: left;
  }

  .accordion_item--data ul {
    list-style: none;
    text-align: left;
    padding: 10px;
  }
</style>

  <div class="accordion_item">
    <div class="accordion_item--header" on:click={handleClick}>{name}</div>
    {#if isOpen}
    <div class="accordion_item--data">
    <ul>
    <li>{`Cuteness: ${cuteness}/10`}</li>
    <li>{`Age: ${age}`}</li>
    </ul>
       <img src={url} alt={name}>
    </div>
    {/if}
  </div>