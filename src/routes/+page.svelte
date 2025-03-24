<script>
	import * as m from '$lib/paraglide/messages.js';
	import AsideContent from '$lib/components/AsideContent.svelte';
	import MainContent from '$lib/components/MainContent.svelte';
</script>

<div id="grid">
	<aside>
		<AsideContent />
	</aside>
	<main>
		<MainContent />
	</main>
	<footer>
		{m.rodo()}
	</footer>
</div>

<style>
	#grid {
		height: 100%;
		display: grid;
		grid-template-columns: auto 1fr;
		grid-template-rows: 1fr auto;
	}
	#grid > * {
		padding: 0.5cm;
		overflow: auto;
	}
	#grid aside {
		background-color: var(--accent-clr);
	}
	#grid main {
		/* background-color: gray; */
	}
	#grid footer {
		padding-block: 0.2cm;
		background-color: whitesmoke;
		color: gray;
		grid-column: 1 / span 2;
		font-size: 7pt;
	}
</style>
