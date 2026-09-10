<script>
	import favicon from '$lib/assets/favicon.jpg';
	let { children } = $props();

	let dropdownOpen = $state(false);

	const items = [
		{ label: 'GamaKay GMK67', href: '/gamakay-gmk67' },
		{ label: 'AULA WIN68HE', href: '/aula-win68he' },
		{ label: 'AULA F75 - Thunder Black', href: '/aula-f75' },
		{ label: 'Razer Basilisk X', href: '/razer-basilisk' },
		{ label: 'AULA F87', href: '/pop-icon' },
		{ label: 'MX Keys Mini — Pale Grey', href: '/mx-keys-mini-pale-grey' },
		{ label: 'AULA F75 - Glacier Blue', href: '/aula-f75-1' }
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
		href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@300;400;500;600&display=swap"
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
		font-family: 'Inter', sans-serif;
		background: #fafafa;
		color: #1a1a1a;
	}
	.site {
		min-height: 100vh;
	}
	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1.5rem 3rem;
		border-bottom: 1px solid #ececec;
		background: #ffffff;
		position: sticky;
		top: 0;
		z-index: 200;
	}
	.wordmark {
		font-family: 'Space Grotesk', sans-serif;
		font-weight: 600;
		letter-spacing: 0.05em;
		color: #1a1a1a;
		text-decoration: none;
	}
	.item-label {
		font-size: 0.85rem;
		letter-spacing: 0.1em;
		color: #6a6a6a;
		text-decoration: none;
	}
	.item-label:hover {
		color: #1a1a1a;
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
		color: #6a6a6a;
	}
	.chevron.open {
		transform: rotate(180deg);
	}
	.menu {
		position: absolute;
		right: 0;
		top: calc(100% + 0.75rem);
		background: #ffffff;
		border: 1px solid #ececec;
		border-radius: 10px;
		box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
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
		color: #6a6a6a;
		text-decoration: none;
		transition:
			color 0.15s,
			background 0.15s;
		white-space: nowrap;
	}
	.menu-item:hover {
		color: #1a1a1a;
		background: #f7f7fb;
	}

	@media (max-width: 768px) {
		nav {
			padding: 1rem 1.5rem;
		}
	}
</style>
