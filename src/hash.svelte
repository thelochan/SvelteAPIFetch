<script lang='ts'>


import { onMount } from "svelte";
let promise;

onMount(() => {
    $: promise = fetch ("http://127.0.0.1:8000/api/v2/mine")
})



</script>

{#await promise}
<div>Wait</div>

{:then results}
<div>{JSON.stringify(results, null, 2)}</div>
{:catch error}
<div> {error.message}</div>
{/await}

