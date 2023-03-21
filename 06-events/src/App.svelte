<script>
  import "./assets/css/style.css";
  import ImageDetail from "./ImageDetail.svelte";

  let scale = 1;
  const handleWheel = (e) => {
    if (e.deltaY < 0) {
      scale += 0.1;
    } else {
      scale -= 0.1;
    }
  }

  let imageDetails = [
    {
      id: 1,
      src: "https://picsum.photos/200/300",
      name: "LittleBig.png",
      size: "3.8MB"
    },
    {
      id: 2,
      src: "https://picsum.photos/201/300",
      name: "DestinyChild.png",
      size: "1.0MB"
    },
    {
      id: 3,
      src: "https://picsum.photos/202/300",
      name: "bigDuck.heic",
      size: "302KB"
    },
    {
      id: 4,
      src: "https://picsum.photos/203/300",
      name: "interstellar-385421555.png",
      size: "1.2GB"
    }
  ]

  const handleDelete = (e) => {
    console.log(e);
    imageDetails = imageDetails.filter(img => img.id !== e.detail);
  }
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8 flex flex-col items-center justify-center">
    <div class="w-32 h-32 p-2 text-sm text-center duration-200 bg-red-500" style="transform: scale({scale})" on:wheel={handleWheel}>Ceci est un texte qui va s'agrandir</div>
    <!-- Ajouter |once ne permettra d'utiliser l'event qu'une fois -->
    <button class="p-2 m-8 text-white bg-red-400 rounded" on:click|once={() => alert('Alerte au gogole !')}>Alerte, Donovan en approche</button>
    <ul class="grid grid-cols-2 gap-x-4 gap-y-8 sm:grid-cols-3 lg:grid-cols-4">
      {#each imageDetails as detail}
        <ImageDetail {...detail} on:deleteImg={handleDelete} />
      {/each}
    </ul>
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
