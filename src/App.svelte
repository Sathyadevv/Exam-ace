<script>
	import '../node_modules/bootstrap/dist/css/bootstrap.min.css'
    import '../node_modules/bootstrap/dist/js/bootstrap.bundle.js'

	import Landing_page from './components/Landing-pag/land-page.svelte'
	import Admin from './components/Dashboard/Admin.svelte'
	import Recent from './components/Dashboard/Recent.svelte'
	import Charts from './components/Dashboard/Charts.svelte'
	import Failed from './components/Dashboard/Failed.svelte'
	import Settings from './components/Dashboard/Settings.svelte'


	import Success from './components/Dashboard/Succes/Success.svelte'
	import SuccessRecent from './components/Dashboard/Succes/Success-Recent.svelte'
	import SuccessChart from './components/Dashboard/Succes/Success-Charts.svelte'
	import SuccessSettings from './components/Dashboard/Succes/Success-Settings.svelte'







	

	let formVal = true;
	

	import router from 'page';
	let current=Landing_page;
	// router('/',()=>{current=Landing_page;formVal=true;})
	// router('/test',()=>{current=Test})


	// router('/app',()=>{current=Admin;formVal=false;})
	// router('/app/home',()=>{current=Admin;formVal=false;})
	// router('/app/recent',()=>{current=Recent ;formVal=false;})
	// router('/app/chart',()=>{current=Charts ;formVal=false;})
	// router('/app/success',()=>{current=Success ;formVal=false;})
	// router('/app/failed',()=>{current=Failed ;formVal=false;})
	// router('/app/settings',()=>{current=Settings ;formVal=false;})



	router('/app',()=>{current=Admin;formVal=false;})
	router('/app/home',()=>{current=Admin;formVal=false;})
	router('/app/recent',()=>{current=Recent ;formVal=false;})
	router('/app/chart',()=>{current=Charts ;formVal=false;})
	router('/app/failed',()=>{current=Failed ;formVal=false;})
	router('/app/settings',()=>{current=Settings ;formVal=false;})





	router('/success',()=>{current=Success ;formVal=false;})
	router('/success/home',()=>{current=Success ;formVal=false;})
	router('/success/recent',()=>{current=SuccessRecent ;formVal=false;})
	router('/success/chart',()=>{current=SuccessChart ;formVal=false;})
	router('/success/settings',()=>{current=SuccessSettings ;formVal=false;})







	
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