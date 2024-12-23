<script>
	import { onMount } from "svelte";
	import { recordRequest } from '$lib/analytics.js';
	// Function to handle navigation events
	function handleNavigation() {
	recordRequest();
	}

	let homeLink;
	let aboutLink;
	let underline;

	// This function will update the active link and the position of the underline
	const setActiveLink = (link) => {
		// Get the link position and size
		const linkRect = link.getBoundingClientRect();
		underline.style.left = `${linkRect.left}px`;
		underline.style.width = `${linkRect.width}px`;
		console.log(linkRect.width);
		console.log(linkRect.left);
	};

	// Call the analytics function on initial page load and after each navigation
	onMount(() => {
		// Set the initial active link to the Home link
		setActiveLink(homeLink);

		handleNavigation();
		afterNavigate(() => {
			handleNavigation();
		});
	});
</script>

<header class="blurred-background">
	<nav>
	  <a
		href="/#wrappedify"
		class="nav-link wrappedify-link"
		bind:this={homeLink}
		on:click={() => setActiveLink(homeLink)}
		>Wrappedify</a
	  >
	  <a
		href="/#about"
		class="nav-link"
		bind:this={aboutLink}
		on:click={() => setActiveLink(aboutLink)}
		>About</a
	  >
	</nav>
	<div class="underline" bind:this={underline}></div>
  </header>

<style>
	header {
	  position: fixed;
	  top: 0;
	  left: 0;
	  right: 0;
	  background-color: #333;
	  z-index: 1000;
	  padding: 20px;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  height: 20px;
	}

	.blurred-background {
		background-color: rgba(0, 0, 0, 0.4); /* Translucent dark background */
		backdrop-filter: blur(10px); /* Blur the background */
		display: flex;
		justify-content: center;
		align-items: center;
		color: white;
		text-align: center;
  	}

	nav {
	  display: flex;
	  gap: 30px;
	}

	.nav-link {
	  color: white;
	  text-decoration: none;
	  font-size: 18px;
	  position: relative;
	  padding: 5px 0;
	}

	.nav-link:hover {
	  color: lightgray;
	}

	.underline {
	  position: absolute;
	  bottom: 0;
	  left: 0;
	  width: 0;
	  height: 2px;
	  background-color: white;
	  border-radius: 3px;
	  transition: width 0.3s ease, left 0.3s ease;
	}

	.wrappedify-link {
		/* Border */
		border: 4px solid transparent;
		border-radius: 20px;
		background:
			linear-gradient(to right, black, black),
			linear-gradient(45deg, #FABA00 , #FA7300, #007FFA, #3D5C7A);
		background-clip: padding-box, border-box;
		background-origin: padding-box, border-box;
		padding: 5px;
	}
</style>
