<script>
	import '../node_modules/bootstrap/dist/css/bootstrap.min.css'
    import '../node_modules/bootstrap/dist/js/bootstrap.bundle.js'

	import Landing_page from '../components/land-page.svelte'
	import Admin from '../components/Admin.svelte'

	

	let formVal = true;
	

	import router from 'page';
	let current='';
	// router('/',()=>{current=Landing_page;formVal=true;})

	router('/app',()=>{current=Admin;formVal=false;})
	// router('/test',()=>{current=Test})



	
    router.start()
</script>

<main>
	{#if formVal}
	<Landing_page />
	{:else}
	<svelte:component this={current==Landing_page ? current='' : current=current} />
    {/if}
</main>

<style>
	
</style>