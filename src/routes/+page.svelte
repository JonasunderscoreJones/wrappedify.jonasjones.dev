<svelte:head>
	<title>Wrappedify</title>
	<meta name="Wrappedify" content="Wrappedify" />
</svelte:head>

<script>
	import { onMount } from "svelte";

	let homeSection;
	let aboutSection;

	onMount(() => {
	  // Scroll behavior when links are clicked (for smooth scrolling)
	  const scrollLinks = document.querySelectorAll('a[href^="#"]');
	  scrollLinks.forEach((link) =>
		link.addEventListener("click", (e) => {
		  e.preventDefault();
		  const target = document.querySelector(link.getAttribute("href"));
		  target.scrollIntoView({ behavior: "smooth" });
		})
	  );
	});
  </script>

  <style>
	section {
	  padding: 100px;
	  height: 100vh;
	}
  </style>

  <section id="home" bind:this={homeSection}>
	<h1>Home</h1>
  </section>

  <section id="about" bind:this={aboutSection}>
	<h1>About</h1>
  </section>
