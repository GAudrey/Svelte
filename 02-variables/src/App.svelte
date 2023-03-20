<script>
  import "./assets/css/style.css";
  let fName = "Sébastion";
  let src = "https://p4.storage.canalblog.com/41/13/993786/99601694.jpg";
  let classe = `${fName === "Sébastion" ? "m-4 border-8 border-yellow-600 w-96" : "w-4"}`;
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <div class="text-xl font-bold text-center text-orange-300">Hello {fName.toUpperCase() + " alias ChoucrouteMan"}
      <img src={src} alt="space cat" class={classe}/>
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
