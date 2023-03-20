<script>
  import "./assets/css/style.css";
  let count = 0;
  let countArray = [];

  // reactive par rapport à la fonction
  const handleClick = () => {
    count++;
    countArray = [...countArray, count]
  }
  // $: reactive par rapport à l'autre variable
  $: double = count*2;
  $: sum = countArray.reduce((acc, current) => acc + current, 0);
  $: if(count >= 10) console.log("Relis ton code");
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <h1 class="text-2xl">How many click can you do with your nose?</h1>
    <p>Je compte avec le nez : {count} {count === 1 || count === 0 ? 'time' : 'times'}</p>
    <p>Double : {double}</p>
    <p>J'ai le sum : {sum}</p>
    <p>({countArray})</p>
    <button class="px-3 py-2 bg-amber-600 text-white" type="button" on:click={handleClick}>Click on me</button>
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
