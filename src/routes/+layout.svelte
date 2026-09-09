<script>
	import favicon from '$lib/assets/favicon.svg';
  import '../styles/stylesheet.css'

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon}>
  <title>Profile card Maarten te Poele</title>
</svelte:head>

{@render children()}
