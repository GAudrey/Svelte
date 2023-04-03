<script>
  import { fly } from "svelte/transition";
  import "./assets/css/style.css";

  let name = "";
  let deathLists = [];
  let anim = true;
  let status = "...Oh, wait";
  const animate = (node, args) => {
    args.cond
      ? fly(node, (args = { x: 200, duration: 1000 }))
      : fly(node, (args = { x: -200, duration: 1000 }));
  };

  $: disabled = name.length < 3 ? true : false;
  const killEnvent = () => {
    deathLists = [...deathLists, name];
    name = "";
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <form class="my-4 shadow-sm p-8" on:submit|preventDefault={killEnvent}>
      <div class="form-control input">
        <div class="flex justify-between">
          <label for="name">Ajouter le nom d'une personne</label>
          <p>Status: {status}</p>
        </div>
        <input type="text" id="name" bind:value={name} />
      </div>
      <button type="submit" class="btn primary mt-4">Ajouter</button>
    </form>
    <div class="mx-auto w-4/5 bg-black text-white shadow-sm p-8 rounded-lg">
      {#each deathLists as deathList}
        <p
          class="mt-2 text-2xl text-center"
          in:fly={{ x: 200, duration: 1000 }}
          out:fly={{ x: -200, duration: 1000 }}
          on:introstart={() => (status = `${deathList} apparaît`)}
          on:outrostart={() => (status = `La liste s'efface`)}
          on:introend={() => (status = `${deathList} est sur la liste`)}
          on:outroend={() => (status = `La liste est vide`)}
        >
          {deathList}
        </p>
      {:else}
        {#if anim}
          <p class="text-3xl text-center" transition:animate={{ anim: false }}>
            No One Is Innocent
          </p>
        {/if}
      {/each}
      {#if deathLists.length}
        <button
          class="btn cancel mt-7 mx-auto block"
          on:click={() => {
            deathLists = [];
            anim = true;
          }}>Save their life</button
        >
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
