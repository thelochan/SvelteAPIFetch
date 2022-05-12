<script>


import Hash from "./hash.svelte";
import Search from "./searchbar.svelte" 

let keyword = "";

</script>

<Search bind:keyword={keyword} />
<Hash keyword={keyword}/>


<style>
	:root {

		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
	}
</style>