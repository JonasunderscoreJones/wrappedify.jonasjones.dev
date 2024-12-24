<svelte:head>
	<title>Wrappedify</title>
	<meta name="Wrappedify" content="Wrappedify" />
</svelte:head>

<script>
	import WrappedPreviews from "$lib/components/WrappedPreviews.svelte";
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
		/* center the content */
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>

<h2>More Data. More Stories. More You. - Wrappedify</h2>

<section id="wrappedify" bind:this={homeSection}>
	<h1>Wrapped</h1>
	<WrappedPreviews />
	<p>View the classic Spotify Wrapped (short version) or the extended one, compiled with a couple extra stats!</p>
</section>

<section id="statistics" bind:this={homeSection}>
	<h1>Statistics</h1>
</section>

<section id="about" bind:this={aboutSection}>
	<h1>About</h1>
</section>
