<script>
	import favicon from '$lib/assets/favicon.jpg';
	let { children } = $props();

	let dropdownOpen = $state(false);

	const items = [
		{ label: 'GamaKay GMK67', href: '/gamakay-gmk67' },
		{ label: 'AULA WIN68HE', href: '/aula-win68he' },
		{ label: 'AULA F75', href: '/aula-f75' },
		{ label: 'Razer Basilisk X', href: '/razer-basilisk' },
		{ label: 'JBL Tune 770NC', href: '/jbl-tune770' },
		{ label: 'Lofree Flow Lite', href: '/lofree-flow-lite' }
	];

	function toggle() {
		dropdownOpen = !dropdownOpen;
	}

	function close() {
		dropdownOpen = false;
	}
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<link
		href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=DM+Sans:wght@300;400;500&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<svelte:window on:click={close} />

<div class="site">
	<nav>
		<a href="/" class="wordmark">Chdkg</a>

		<div class="dropdown" on:click|stopPropagation>
			<button class="item-label trigger" on:click={toggle} aria-expanded={dropdownOpen}>
				Products
				<svg
					class="chevron"
					class:open={dropdownOpen}
					width="10"
					height="10"
					viewBox="0 0 10 10"
					fill="none"
				>
					<path
						d="M2 3.5L5 6.5L8 3.5"
						stroke="currentColor"
						stroke-width="1.2"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</button>

			{#if dropdownOpen}
				<ul class="menu">
					{#each items as item}
						<li>
							<a
								href={item.href}
								target="_blank"
								rel="noopener noreferrer"
								class="menu-item"
								on:click={close}
							>
								{item.label}
							</a>
						</li>
					{/each}
				</ul>
			{/if}
		</div>
	</nav>
	{@render children()}
</div>

<style>
	:global(*, *::before, *::after) {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}
	:global(body) {
		font-family: 'DM Sans', sans-serif;
		background: #0e0d0b;
		color: #f0ede6;
	}
	.site {
		min-height: 100vh;
	}
	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1.5rem 3rem;
		border-bottom: 1px solid #2a2a28;
		position: sticky;
		top: 0;
		background: #0e0d0b;
		z-index: 200;
	}
	.wordmark {
		font-family: 'Playfair Display', serif;
		font-size: 1.1rem;
		letter-spacing: 0.25em;
		text-decoration: none;
		color: #f0ede6;
	}
	.item-label {
		font-size: 0.85rem;
		letter-spacing: 0.1em;
		color: #8a8a88;
		text-decoration: none;
	}
	.item-label:hover {
		color: #f0ede6;
	}
	.dropdown {
		position: relative;
	}
	.trigger {
		display: flex;
		align-items: center;
		gap: 0.35rem;
		background: none;
		border: none;
		cursor: pointer;
		padding: 0;
		transition: color 0.2s;
	}
	.chevron {
		transition: transform 0.2s ease;
		color: #8a8a88;
	}
	.chevron.open {
		transform: rotate(180deg);
	}
	.menu {
		position: absolute;
		right: 0;
		top: calc(100% + 0.75rem);
		background: #141412;
		border: 1px solid #2a2a28;
		list-style: none;
		min-width: 200px;
		padding: 0.6rem 0;
		animation: fadeIn 0.15s ease;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
			transform: translateY(-4px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.menu-item {
		display: block;
		padding: 0.8rem 1.5rem;
		font-size: 0.9rem;
		letter-spacing: 0.08em;
		color: #8a8a88;
		text-decoration: none;
		transition:
			color 0.15s,
			background 0.15s;
		white-space: nowrap;
	}
	.menu-item:hover {
		color: #f0ede6;
		background: #1e1e1c;
	}

	@media (max-width: 768px) {
		nav {
			padding: 1rem 1.5rem;
		}
	}
</style>
