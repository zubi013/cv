<script>
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import { onMount } from 'svelte';

	let { children } = $props();

	let cv_content = $state();
	let doc;

	onMount(() => {
		doc = document.createDocumentFragment();
	});

	function print() {
		const clone = cv_content.cloneNode(true);
		doc.replaceChildren(...document.body.children);
		document.body.replaceChildren(clone);
		window.print();
		document.body.replaceChildren(...doc.children);
	}
</script>

<ParaglideJS {i18n}>
	<button onclick={print}>PRINT</button>

	<div bind:this={cv_content}>{@render children?.()}</div>
</ParaglideJS>

<style>
	:global(body) {
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		margin: 0;
		background-color: salmon;
		padding: 20px 20px 160px 20px;
		--accent-clr: rgb(22, 33, 60);
		li {
			color: red;
		}
		@media print {
			padding: 0;
			* {
				display: none;
			}
			div {
				margin: 0;
				display: block;
				-webkit-print-color-adjust: exact;
				color-adjust: exact;
			}
		}
	}
	div {
		margin: 20px;
		margin-inline: auto;
		width: 21cm;
		height: 29.7cm;
		background-color: white;
	}
</style>
