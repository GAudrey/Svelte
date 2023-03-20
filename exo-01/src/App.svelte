<script>
  import "./assets/css/style.css";
  import RandomVeggie from "./RandomVeggie.svelte";
  import Veggies from "./Veggies.svelte";

  const vegetables = [
    {
      id: 1,
      name: "carotte",
      season: "été",
    },
    {
      id: 2,
      name: "tomate",
      season: "été",
    },
    {
      id: 3,
      name: "courgette",
      season: "été",
    },
    {
      id: 4,
      name: "salade",
      season: "été",
    },
    {
      id: 5,
      name: "salsifit",
      season: "été",
    },
    {
      id: 6,
      name: "betrave",
      season: "été",
    },
    {
      id: 7,
      name: "haricot",
      season: "été",
    },
    {
      id: 8,
      name: "celeri",
      season: "été",
    },
    {
      id: 9,
      name: "chicon",
      season: "été",
    },
    {
      id: 10,
      name: "poivron",
      season: "été",
    },
  ];
  let isClicked = false;
  let random;
  const listedVegetable = () => {
    isClicked = true;
  }
  const onClickRandom = () => {
    isClicked = false;
    return random = Math.ceil(Math.random() * vegetables.length);
  }
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <div class="flex justify-evenly">
      <button type="button" class="px-4 py-3 rounded bg-amber-600 text-white duration-200 hover:bg-amber-300" on:click={listedVegetable}>Show vegetables' list</button>
      <button type="button" class="px-4 py-3 rounded bg-blue-600 text-white duration-200 hover:bg-blue-300" on:click={onClickRandom}>Random vegetable</button>
    </div>

    <div>
      {#each vegetables as veggie}
        {#if isClicked}
          <Veggies {...veggie} />
        {:else}
          {#if random === veggie.id}
            <RandomVeggie {veggie}/>
          {/if}
        {/if}
      {/each}
    </div>
  </main>
</div>

<style>
  .animation-image {
    @apply cursor-pointer duration-200;
  }

  .animation-image:hover {
    @apply scale-75;
  }
</style>
