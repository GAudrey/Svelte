<script>
  import "./assets/css/style.css";
  import Kid from "./Kid.svelte";
  import format from "date-fns/format";

  let user = {loggedIn : false};
  let logs = [];

  const toggleLogin = () => {
    user.loggedIn = !user.loggedIn;
    logs = [...logs, {isConnected: user.loggedIn, time: format(new Date(), "HH:mm:ss")},];
  }
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <Kid />
    <Kid password="goulagustre"/>
    {#if logs}
      {#each logs as {isConnected, time}, index}
        <p class="mt-2 ml-4">{index + 1}.{isConnected ? "Connexion" : "Déconnexion"} à {time}.</p>
      {/each}
    {/if}
    
    {#if user.loggedIn}
      <button on:click={toggleLogin} type="button" class="px-4 py-2 rounded shadow bg-red-600 text-white duration-200 hover:bg-red-300">Logout</button>
    {:else}
      <button on:click={toggleLogin} type="button" class="px-4 py-2 rounded shadow bg-green-600 text-white duration-200 hover:bg-green-300">Login</button>
    {/if}
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
