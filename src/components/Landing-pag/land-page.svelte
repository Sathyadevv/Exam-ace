<script>
  import Navbar from "./nav-bar.svelte";
  import Footer from "./footer.svelte";
  import Home from "./Home/home.svelte";
  import About from "./About/about.svelte";
  import Contact from "./Contact/contact.svelte";
  import Sign_in_form from "./Sign-in/sigin-form.svelte";
  import Sign_up_form from "./Sign-up/signup-form.svelte";

  import router from "page";
  let current = "";
  router("/", () => {
    current = Home;
  });
  router("/about", () => {
    current = About;
  });
  router("/contact", () => {
    current = Contact;
  });
  router("/sign-in", () => {
    current = Sign_in_form;
  });
  router("/sign-up", () => {
    current = Sign_up_form;
  });

  router.start();
</script>

<main>
  <Navbar />
  <svelte:component this={current} />
  <Footer />
</main>
