<script>
  import "./assets/css/style.css";
  import JokesAPI from "blagues-api";
  import { onMount } from "svelte";
  import { linear } from "svelte/easing";
  import { fly, fade } from "svelte/transition";

  let jokes = new JokesAPI(
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiMjA3MTkwNzgyNjczODEzNTA0IiwibGltaXQiOjEwMCwia2V5IjoibEEwa3lVc3cybm1UdUhMRXk3WnJsYlAxemF4QWRwczhYRk05R1FkZ3ljZlhocmtTbzkiLCJjcmVhdGVkX2F0IjoiMjAyMy0wMS0xN1QwMTo1MDoyMCswMDowMCIsImlhdCI6MTY3MzkyMDIyMH0.uYcTZpM9SByWVClV0Jrz3U3vQtG18xiUMxKhtQPP5y4"
  );

  let joke;
  onMount(async () => {
    joke = await jokes.random();
  });

  let toggleAnswer = false;

  const showAnswer = () => {
    toggleAnswer = true;
  };

  const newJoke = async () => {
    joke = "";
    joke = await jokes.random();
    toggleAnswer = false;
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    {#if joke}
      <p
        in:fly={{ x: 200, duration: 1500 }}
        out:fade={{ duration: 1500, easing: linear }}
      >
        {joke.joke}
      </p>
      {#if toggleAnswer}
        <p>
          {joke.answer}
        </p>
        <button type="button" class="btn warning" on:click={newJoke}
          >Nouvelle blague</button
        >
      {:else}
        <button type="button" class="btn primary" on:click={showAnswer}
          >Montrer la réponse</button
        >
      {/if}
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
