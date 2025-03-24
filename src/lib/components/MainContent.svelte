<script>
	import * as m from '$lib/paraglide/messages.js';
	const header = {
		name: 'Kacper Zubrzyński',
		profession: 'Fullstack Dev/Graphic Designer'
	};
	const sections = [
		{
			title: m.profile(),
			points: [{ description: m.profile_description() }]
		},
		{
			title: m.abilities(),
			points: [
				{ name: m.tech(), aftername: 'SvelteKit, Drizzle ORM, SQL, JavaScript, HTML, CSS, Python' },
				{
					name: m.graphic(),
					aftername: 'Blender, Figma, Photoshop, Illustrator, InDesign, Affinity'
				},
				{ name: m.webdesign() }
			]
		},
		{
			title: m.exp(),
			points: [
				{
					name: m.exp_1(),
					aftername: '07.2021 – 07.2024',
					bulletpoint: [m.exp_1_b1(), m.exp_1_b2(), m.exp_1_b3()]
				},
				{
					name: m.exp_2(),
					aftername: '07.2021 – 07.2024',
					bulletpoint: [m.exp_2_b1(), m.exp_2_b2(), m.exp_2_b3(), m.exp_2_b4()]
				},
				{ name: m.exp_3(), aftername: '07.2021 – 07.2024', bulletpoint: [m.exp_3_b1()] }
			]
		},
		{
			title: m.education(),
			aftername: '07.2020',
			points: [{ name: m.school(), aftername: m.degree() }]
		},
		{
			title: m.projects(),
			points: [{ bulletpoint: [m.project_1(), m.project_2(), m.project_3()] }]
		},
		{
			title: m.lang(),
			points: [
				{ name: m.pl_lang(), aftername: 'native' },
				{ name: m.eng_lang(), aftername: 'B2' }
			]
		}
	];
</script>

<h1>
	{header.name}
	<p>{header.profession}</p>
</h1>
{#each sections as s}
	<h2>{s.title}</h2>
	{#if s.points}
		<ul class="no-bullets items-ul">
			{#each s.points as p}
				{@render items(p.name, p.aftername, p.description, p.bulletpoint)}
			{/each}
		</ul>
	{/if}
{/each}
{#snippet items(name = null, aftername = null, description = null, bullets = null)}
	<li>
		{#if name || aftername}
			<div class="item-header">
				{#if name}
					<strong>{name}</strong>
				{/if}
				{#if aftername}
					<span>{aftername}</span>
				{/if}
			</div>
		{/if}
		{#if description}
			<p>{description}</p>
		{/if}

		{#if bullets !== null}
			<ul>
				{#each bullets as b}
					<li>{b}</li>
				{/each}
			</ul>
		{/if}
	</li>
{/snippet}

<style>
	h1 {
		font-size: 1cm;
		margin: 0;
		margin-bottom: 30px;
		color: var(--accent-clr);
	}
	h1 p {
		margin: 0;
		font-size: 0.5cm;
		text-indent: 0;
		color: gray;
	}
	h2 {
		color: whitesmoke;
		border-radius: 100px;
		padding-block: 0.17em 0.32em;
		padding-inline: 0.8em;
		margin-block: 8px;
		background-color: var(--accent-clr);
		font-size: 0.35cm;
	}
	.no-bullets {
		list-style: none;
		padding: 0;
	}
	p,
	li {
		font-size: 9pt;
	}
	p {
		text-indent: 1.5em;
		margin: 0;
	}
	.item-header {
		display: grid;
		margin: 8px;
	}
	.item-header span {
		color: gray;
	}
	ul {
		margin: 0;
	}
</style>
