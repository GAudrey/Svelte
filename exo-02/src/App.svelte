<script>
  import "./assets/css/style.css";
  import ListCountry from "./ListCountry.svelte";

  let countries = [
    {
      id: 1,
      src: "https://www.flagsapi.com/BE/shiny/64.png",
      country: "Belgium"
    },
    {
      id: 2,
      src: "https://www.flagsapi.com/IT/shiny/64.png",
      country: "Italy"
    },
    {
      id: 3,
      src: "https://www.flagsapi.com/FR/shiny/64.png",
      country: "France"
    },
    {
      id: 4,
      src: "https://www.flagsapi.com/GA/shiny/64.png",
      country: "Gabon"
    },
    {
      id: 5,
      src: "https://www.flagsapi.com/US/shiny/64.png",
      country: "United State"
    },
    {
      id: 6,
      src: "https://www.flagsapi.com/SR/shiny/64.png",
      country: "Suriname"
    },
  ]

  let showSelect = false;
  
  let selectedCountry;
  const handleCountry = (e) => {
    selectedCountry = countries.find(pick => pick.id === e.detail);
    showSelect = false;
  }
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <div class="relative inline-block text-left">
      <div>
        <button type="button" class="inline-flex justify-center w-full rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none" on:click={() => showSelect = !showSelect}>
          {#if selectedCountry}
            <img src={selectedCountry.src} alt={selectedCountry.country + " flag"} class="w-5 mr-2" />
            <p class="text-sm text-gray-700">
                {selectedCountry.country}
            </p>
          {:else}
            Select a country
          {/if}  
          <svg class="-mr-1 ml-2 h-5 w-5 {showSelect ? 'rotate-180' : ''}" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>
      {#if showSelect}
        <div class="origin-top-left absolute left-0 mt-2 w-56 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 focus:outline-none">
          {#each countries as country}
            <ListCountry {...country} on:select={handleCountry}/>
          {/each}
        </div>
      {/if}
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
