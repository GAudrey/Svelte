<script>
    import { createEventDispatcher } from "svelte";

    export let id, src, country;

    const dispatch = createEventDispatcher();
</script>

<div class="flex my-2 cursor-pointer" on:click={() => dispatch('select', id)}>
    <img {src} alt={country + " flag"} class="w-5 mx-2" />
    <p class="text-sm text-gray-700">
        {country}
    </p>
</div>