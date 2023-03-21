<script>
    import { createEventDispatcher } from "svelte";

    export let id, name, src, size;
    const dispatch = createEventDispatcher();
    const deleteThisImg = () => {
        dispatch('deleteImg', id);
    }
</script>

<li class="relative">
    <div class="block w-full overflow-hidden bg-gray-100 rounded-lg group aspect-w-10 aspect-h-7 focus-within:ring-2 focus-within:ring-offset-gray-100 focus-within:ring-indigo-500">
        <img src={src} alt="" class="object-cover point-events-none group-hover:opacity-75" />
        <!-- <button type="button" class="absolute inset-8 focus:outline-none">
            <span class="sr-only">View details for {name}</span>
        </button> -->
        <p class="block mt-2 text-sm font-medium text-gray-900 pointer-events-none">{name}</p>
        <p class="block mt-2 text-sm font-medium text-gray-500 pointer-events-none">{size}</p>
        <button type="button" class="block px-2 py-1 my-4 mx-auto text-sm text-right text-white duration-200 bg-red-500 hover:bg-red-300" on:click={deleteThisImg}>Delete</button>
    </div>
</li>