<script>
	import '../node_modules/bootstrap/dist/css/bootstrap.min.css'
    import '../node_modules/bootstrap/dist/js/bootstrap.bundle.js'

	import Navbar from './nav-bar.svelte'
	import Home from './home.svelte'
	import About from './about.svelte'
	import Contact from './contact.svelte'
	import Footer from './footer.svelte'
	import Sign_in_form from './sigin-form.svelte'
	import Sign_up_form from './signup-form.svelte'


	import router from 'page';
	let current='';
	router('/',()=>{current=Home})
	router('/about',()=>{current=About})
	router('/contact',()=>{current=Contact})
	router('/sign-in',()=>{current=Sign_in_form})
	router('/sign-up',()=>{current=Sign_up_form})



	
    router.start()
</script>

<main>
	
	<Navbar />
	<svelte:component this={current} />
	<Footer />
</main>
