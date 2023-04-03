<script>
  import "./assets/css/style.css";
  import CardDetail from "./CardDetail.svelte";
  import FormDetail from "./FormDetail.svelte";

  let name = "My little BigSebou";
  // fonctionne avec le premier input
  // $: newValue = (e) => {
  //   return (name = e.target.value);
  // };

  const humanDetail = {
    name: "Mark Henry",
    gender: "binary",
    imageURL: "https://picsum.photos/900/600",
    free: false,
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- Fonctionne mais plus simple en svelte -->
    <!-- <input
      type="text"
      class="border-2 border-orange-300 rounded mx-4"
      value={name}
      on:input={newValue}
    /> -->

    <div class="flex gap-2">
      <input
        type="text"
        class="border-2 border-orange-300 rounded mx-4"
        bind:value={name}
      />
      <p>{name}</p>
    </div>
    <FormDetail
      bind:name={humanDetail.name}
      bind:imageURL={humanDetail.imageURL}
      bind:gender={humanDetail.gender}
      bind:free={humanDetail.free}
    />
    <CardDetail {...humanDetail} />
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
