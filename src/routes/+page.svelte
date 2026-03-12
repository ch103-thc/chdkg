<script>
	const products = [
		{
			id: 1,
			category: 'Keyboards',
			name: 'GamaKay GMK67',
			fullName: 'GamaKay GMK67 Customized Mechanical Keyboard',
			tagline: 'Built for enthusiasts. Ready out of the box.',
			price: 179.9,
			badge: null,
			img: 'img/gamakay-gmk67.png',
			href: '/gamakay-gmk67'
		},
		{
			id: 2,
			category: 'Keyboards',
			name: 'AULA WIN68HE',
			fullName: 'AULA WIN68HE Wireless Mechanical Keyboard',
			tagline: 'Hall effect precision. Wire-free freedom.',
			price: 100,
			badge: null,
			img: 'img/aula-win68he.png',
			href: '/aula-win68he'
		},
		{
			id: 3,
			category: 'Keyboards',
			name: 'AULA F75',
			fullName: 'AULA F75 Wireless Mechanical Keyboard',
			tagline: 'Compact. Precise. Yours.',
			price: 60,
			badge: null,
			img: 'img/aula-f75.png',
			href: '/aula-f75'
		},
		{
			id: 4,
			category: 'Mice',
			name: 'Logitech M240',
			fullName: 'Logitech M240 Silent Bluetooth Mouse',
			tagline: 'Whisper-quiet. All-day comfort.',
			price: 21,
			badge: null,
			img: 'img/logitech-m240.png',
			href: '/logitech-m240'
		},
		{
			id: 5,
			category: 'Mice',
			name: 'Razer Basilisk X',
			fullName: 'Razer Basilisk X HyperSpeed Wireless Gaming Mouse',
			tagline: 'HyperSpeed wireless. Built to win.',
			price: 60,
			badge: null,
			img: 'img/razer-basilisk.png',
			href: '/razer-basilisk'
		},
		{
			id: 6,
			category: 'Audio',
			name: 'JBL Tune 770NC',
			fullName: 'JBL Tune 770NC Wireless Over-Ear Headphones',
			tagline: 'Noise cancelled. Bass amplified.',
			price: 100,
			badge: null,
			img: 'img/jbl-tune770.png',
			href: '/jbl-tune770'
		},
		{
			id: 7,
			category: 'Mice',
			name: 'Logitech Signature M650',
			fullName: 'Logitech Signature M650 Wireless Mouse',
			tagline: 'Smart scrolling. Comfortable control.',
			price: 44,
			badge: null,
			img: 'img/logitech-m650.png',
			href: '/logitech-m650'
		},
		{
			id: 8,
			category: 'Mice',
			name: 'UGREEN Ergonomic Mouse',
			fullName: 'UGREEN Ergonomic Wireless Mouse',
			tagline: 'Ergonomic design. Smooth wireless performance.',
			price: 15,
			badge: null,
			img: 'img/ugreen-mouse.png',
			href: '/ugreen-ergonomic-mouse'
		}
	];

	// Collect unique categories for filter tabs
	const collections = ['All', ...new Set(products.map((p) => p.category))];

	let activeFilter = $state('All');
	let hoveredId = $state(null);

	let filtered = $derived(
		activeFilter === 'All' ? products : products.filter((p) => p.category === activeFilter)
	);

	const badgeColors = {
		New: '#4a9eff',
		Popular: '#e8a838',
		Hot: '#e85238',
		Sale: '#5cb87a'
	};
</script>

<main>
	<!-- Header -->
	<header>
		<div class="header-inner">
			<div class="brand">
				<span class="brand-mark">✦</span>
				<span class="brand-name">Catalog</span>
			</div>
			<nav class="filter-tabs">
				{#each collections as col}
					<button
						class="tab"
						class:active={activeFilter === col}
						onclick={() => (activeFilter = col)}
					>
						{col}
					</button>
				{/each}
			</nav>
			<div class="header-meta">
				<span class="product-count">{filtered.length} items</span>
			</div>
		</div>
	</header>

	<!-- Hero strip -->
	<section class="hero-strip">
		<p class="hero-label">Catalog</p>
		<h1 class="hero-title">Gear & Peripherals</h1>
		<p class="hero-sub">Keyboards, mice, audio — curated gear for your setup.</p>
	</section>

	<!-- Grid -->
	<section class="catalog-grid">
		{#each filtered as product (product.id)}
			<article
				class="product-card"
				class:hovered={hoveredId === product.id}
				onmouseenter={() => (hoveredId = product.id)}
				onmouseleave={() => (hoveredId = null)}
			>
				<!-- Image -->
				<div class="card-image">
					<img src={product.img} alt={product.name} />
					{#if product.badge}
						<span class="badge" style="background: {badgeColors[product.badge] ?? '#888'}">
							{product.badge}
						</span>
					{/if}
					<a href={product.href} target="_blank" rel="noopener noreferrer" class="quick-buy">
						Buy Now →
					</a>
				</div>

				<!-- Info -->
				<div class="card-info">
					<div class="card-meta">
						<span class="card-collection">{product.category}</span>
					</div>
					<h2 class="card-name">{product.name}</h2>
					<p class="card-fullname">{product.fullName}</p>
					<p class="card-tagline">{product.tagline}</p>
					<div class="card-footer">
						<span class="card-price">
							{#if product.price}
								${product.price} <span class="currency">SGD</span>
							{:else}
								<span class="price-dm">DM for price</span>
							{/if}
						</span>
						<a href={product.href} target="_blank" rel="noopener noreferrer" class="card-btn">
							View
						</a>
					</div>
				</div>
			</article>
		{/each}
	</section>

	<footer>
		<span class="footer-mark">✦</span>
		<p>All prices in SGD. Sold via Carousell with Buyer Protection.</p>
	</footer>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;1,400&family=DM+Sans:wght@300;400;500&display=swap');

	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	:global(body) {
		background: #0e0d0b;
		color: #f0ede6;
		font-family: 'DM Sans', sans-serif;
		-webkit-font-smoothing: antialiased;
	}

	/* ── Header ── */
	header {
		position: sticky;
		top: 0;
		z-index: 50;
		background: rgba(14, 13, 11, 0.92);
		backdrop-filter: blur(12px);
		border-bottom: 1px solid #2a2a28;
	}
	.header-inner {
		max-width: 1400px;
		margin: 0 auto;
		padding: 0 3rem;
		height: 65px;
		display: flex;
		align-items: center;
		gap: 2rem;
	}
	.brand {
		display: flex;
		align-items: center;
		gap: 0.6rem;
		flex-shrink: 0;
	}
	.brand-mark {
		color: #6a6a68;
		font-size: 0.7rem;
	}
	.brand-name {
		font-family: 'Playfair Display', serif;
		font-size: 1.1rem;
		letter-spacing: 0.05em;
	}
	.filter-tabs {
		display: flex;
		gap: 0.25rem;
		flex: 1;
		justify-content: center;
	}
	.tab {
		background: none;
		border: none;
		color: #6a6a68;
		font-family: 'DM Sans', sans-serif;
		font-size: 0.78rem;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		padding: 0.4rem 1rem;
		cursor: pointer;
		border-radius: 2px;
		transition:
			color 0.15s,
			background 0.15s;
	}
	.tab:hover {
		color: #c0c0be;
	}
	.tab.active {
		color: #f0ede6;
		background: #1e1e1c;
	}
	.header-meta {
		flex-shrink: 0;
	}
	.product-count {
		font-size: 0.75rem;
		color: #4a4a48;
		letter-spacing: 0.1em;
	}

	/* ── Hero strip ── */
	.hero-strip {
		max-width: 1400px;
		margin: 0 auto;
		padding: 4rem 3rem 3rem;
		border-bottom: 1px solid #1e1e1c;
	}
	.hero-label {
		font-size: 0.7rem;
		letter-spacing: 0.25em;
		color: #4a4a48;
		text-transform: uppercase;
		margin-bottom: 0.6rem;
	}
	.hero-title {
		font-family: 'Playfair Display', serif;
		font-size: clamp(2.2rem, 5vw, 4rem);
		font-weight: 400;
		line-height: 1;
		margin-bottom: 0.75rem;
	}
	.hero-sub {
		font-size: 0.9rem;
		color: #6a6a68;
		font-style: italic;
	}

	/* ── Grid ── */
	.catalog-grid {
		max-width: 1400px;
		margin: 0 auto;
		padding: 3rem;
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
		gap: 1.5px;
		background: #1a1a18;
		border: 1px solid #1a1a18;
	}

	/* ── Card ── */
	.product-card {
		background: #0e0d0b;
		display: flex;
		flex-direction: column;
		transition: background 0.2s;
		cursor: default;
	}
	.product-card.hovered {
		background: #141412;
	}

	.card-image {
		position: relative;
		aspect-ratio: 4 / 3;
		overflow: hidden;
		background: #141412;
	}
	.card-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition:
			transform 0.5s ease,
			filter 0.3s ease;
		filter: brightness(0.9);
	}
	.product-card.hovered .card-image img {
		transform: scale(1.04);
		filter: brightness(1);
	}

	.badge {
		position: absolute;
		top: 1rem;
		left: 1rem;
		font-size: 0.65rem;
		font-weight: 600;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		padding: 0.25rem 0.6rem;
		border-radius: 2px;
		color: #0e0d0b;
	}

	.quick-buy {
		position: absolute;
		bottom: 1rem;
		left: 50%;
		transform: translateX(-50%) translateY(8px);
		background: #f0ede6;
		color: #0e0d0b;
		text-decoration: none;
		font-size: 0.72rem;
		font-weight: 600;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		padding: 0.5rem 1.2rem;
		border-radius: 2px;
		white-space: nowrap;
		opacity: 0;
		transition:
			opacity 0.2s,
			transform 0.2s;
	}
	.product-card.hovered .quick-buy {
		opacity: 1;
		transform: translateX(-50%) translateY(0);
	}

	.card-info {
		padding: 1.4rem 1.5rem 1.5rem;
		display: flex;
		flex-direction: column;
		gap: 0.4rem;
		flex: 1;
		border-top: 1px solid #1a1a18;
	}
	.card-meta {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.card-collection {
		font-size: 0.68rem;
		letter-spacing: 0.18em;
		color: #4a4a48;
		text-transform: uppercase;
	}
	.card-color {
		font-size: 0.68rem;
		color: #4a4a48;
		letter-spacing: 0.05em;
	}
	.card-name {
		font-family: 'Playfair Display', serif;
		font-size: 1.35rem;
		font-weight: 400;
		line-height: 1.2;
		color: #f0ede6;
	}
	.card-fullname {
		font-size: 0.72rem;
		color: #3a3a38;
		line-height: 1.4;
		margin-top: -0.1rem;
	}
	.price-dm {
		font-size: 0.75rem;
		color: #5a5a58;
		font-style: italic;
		letter-spacing: 0.03em;
	}
	.card-tagline {
		font-size: 0.78rem;
		color: #5a5a58;
		font-style: italic;
		line-height: 1.5;
	}
	.card-footer {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-top: 0.75rem;
		padding-top: 0.75rem;
		border-top: 1px solid #1e1e1c;
	}
	.card-price {
		font-size: 1rem;
		font-weight: 500;
		letter-spacing: 0.04em;
	}
	.currency {
		font-size: 0.7rem;
		color: #6a6a68;
		font-weight: 400;
	}
	.card-btn {
		display: inline-block;
		border: 1px solid #3a3a38;
		color: #a0a09e;
		text-decoration: none;
		font-size: 0.72rem;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		padding: 0.4rem 1rem;
		border-radius: 2px;
		transition:
			border-color 0.15s,
			color 0.15s,
			background 0.15s;
	}
	.card-btn:hover {
		border-color: #f0ede6;
		color: #f0ede6;
		background: #1a1a18;
	}

	/* ── Footer ── */
	footer {
		max-width: 1400px;
		margin: 0 auto;
		padding: 2.5rem 3rem;
		display: flex;
		align-items: center;
		gap: 1rem;
		border-top: 1px solid #1a1a18;
	}
	.footer-mark {
		color: #3a3a38;
		font-size: 0.7rem;
	}
	footer p {
		font-size: 0.75rem;
		color: #3a3a38;
		letter-spacing: 0.05em;
	}

	/* ── Responsive ── */
	@media (max-width: 768px) {
		.header-inner {
			padding: 0 1.5rem;
			gap: 1rem;
		}
		.filter-tabs {
			gap: 0;
		}
		.tab {
			padding: 0.4rem 0.6rem;
			font-size: 0.7rem;
		}
		.hero-strip {
			padding: 2.5rem 1.5rem 2rem;
		}
		.catalog-grid {
			padding: 0;
			grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
		}
		footer {
			padding: 2rem 1.5rem;
		}
	}
</style>
