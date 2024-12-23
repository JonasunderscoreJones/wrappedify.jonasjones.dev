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

<header>
	<nav>
	  <a
		href="/"
		class="nav-link"
		bind:this={homeLink}
		on:click={() => setActiveLink(homeLink)}
		>Home</a
	  >
	  <a
		href="/"
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
	  height: 60px;
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
	  transition: width 0.3s ease, left 0.3s ease;
	}
  </style>
