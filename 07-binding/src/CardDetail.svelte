<script>
  export let name;
  export let gender;
  export let imageURL;
  export let free;
</script>

<div class="border bg-gray-200 rounded shadow-sm mt-4">
  <img
    src={imageURL}
    alt="picture of {name}"
    class="object-cover object-center w-full h-64 rounded-t"
  />
  <div class="flex flex-col items-center py-8">
    <h2 class="text-3xl font-bold text-gray-400">{name}</h2>
    <h3 class="text-xl font-bold text-indigo-300">{gender}</h3>
    <p class="mt-4 text-2xl font-bold">{free ? "Free" : "Not free"} tonight</p>
  </div>
</div>
