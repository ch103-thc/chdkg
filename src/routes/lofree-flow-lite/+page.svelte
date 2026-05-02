<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/lofree-flow-lite-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = [
		'/img/lofree-flow-lite-1.jpg',
		'/img/lofree-flow-lite-2.jpg',
		'/img/lofree-flow-lite-3.jpg',
		'/img/lofree-flow-lite.MP4'
	];

	const product = {
		name: 'Lofree Flow Lite Mechanical Keyboard',
		tagline: 'Featherlight. Fluid. Flawless.',
		price: 99.9,
		description:
			'The Lofree Flow Lite brings the beloved Flow experience to a lighter, more portable form — featuring Specter linear switches, a gasket-mount structure, and wireless tri-mode connectivity in a sleek white finish.'
	};

	const features = [
		'Specter linear switches — smooth, factory-lubed',
		'Gasket mount with silicone dampening',
		'Per-key RGB with dynamic lighting effects',
		'Tri-mode: 2.4GHz wireless, Bluetooth 5.0, USB-C wired',
		'Hot-swappable',
		'Low-profile PBT keycaps',
		'Compact 75% layout with function row'
	];

	const specs = [
		{ label: 'Layout', value: '75% (84 keys)' },
		{ label: 'Switch', value: 'Specter Linear (hot-swap)' },
		{ label: 'Battery', value: '2000mAh' },
		{ label: 'Structure', value: 'Gasket mount' },
		{ label: 'Connectivity', value: '2.4GHz / BT 5.0 / USB-C' },
		{ label: 'Polling Rate', value: '1000Hz' },
		{ label: 'Weight', value: '~680g' },
		{ label: 'Colour', value: 'White' }
	];

	const inbox = ['Lofree Flow Lite Keyboard', '2.4GHz USB Dongle', 'USB-C Cable', 'User Manual'];

	const faqs = [
		{
			q: 'How can I pay for this listing?',
			a: "Click on the above 'Buy Now' button to proceed to Carousell. Once you're on Carousell, tap on the 'Buy' button to pay securely via Carousell. Pay directly with your credit/debit card, DBS PayLah! or PayNow — no additional set-ups or wallet top-ups needed."
		},
		{
			q: 'What is Buyer Protection?',
			a: "Your purchase is covered by Buyer Protection when you pay via the 'Buy' button. This means you'll get a full refund if the item doesn't arrive, is damaged during delivery, or is not what you saw in the listing.<br><a href='https://support.carousell.com/hc/en-us/articles/360038048693--Singapore-What-does-Buyer-Protection-cover' target='_blank' rel='noopener noreferrer'>Learn more</a>"
		},
		{
			q: 'How do I request for a return or refund?',
			a: "Just tap on 'Return/refund' on your order details page if something goes wrong with your order. Carousell will reach out to you via email within 24h to resolve the issue.<br><a href='https://support.carousell.com/hc/en-us/articles/360001548627--Singapore-How-do-I-raise-a-return-refund-request' target='_blank' rel='noopener noreferrer'>Learn more</a>"
		},
		{
			q: 'What switches does it use?',
			a: 'It comes with Specter linear switches — smooth, factory-lubed linears designed by Lofree for a light, fast keystroke. The PCB is hot-swappable so you can change switches without soldering.'
		},
		{
			q: 'What type of connection does it support?',
			a: 'It supports tri-mode connectivity: 2.4GHz wireless, Bluetooth 5.0, and USB-C wired.'
		},
		{
			q: 'How long does shipping take?',
			a: '2–4 days after seller ships your order, with tracking.'
		}
	];

	let openFaq = $state(null);
</script>

<main>
	<section class="product">
		<div class="visual">
			<div class="main-image">
				{#if isVideo}
					<video
						src={activeMedia}
						controls
						autoplay
						loop
						poster="/img/lofree-flow-lite-video-thumb.png"
					/>
				{:else}
					<img src={activeMedia} alt="Lofree Flow Lite Mechanical Keyboard" />
				{/if}
			</div>
			<div class="thumbnails">
				{#each media as item}
					<button
						class="thumb-btn"
						class:active={activeMedia === item}
						onclick={() => (activeMedia = item)}
					>
						{#if item.endsWith('.MP4')}
							<div class="thumb-video-wrap">
								<video src={item} muted preload="metadata" />
								<span class="play-icon">{activeMedia === item ? '⏸' : '▶'}</span>
							</div>
						{:else}
							<img src={item} alt="Lofree Flow Lite view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">Lofree Flow Lite — White</p>
		</div>

		<div class="details">
			<p class="collection">Flow Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a
				href="https://www.carousell.sg/p/lofree-flow-lite-1429884801/?referrer_source=me_page"
				target="_blank"
				rel="noopener noreferrer"
				class="buy-btn"
			>
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>75% Compact Layout</strong> – All the keys you need, none you don't. Clean, minimal,
					desk-friendly.
				</li>
				<li>
					<strong>Specter Linear Switches</strong> – Silky-smooth keystrokes with a light actuation force.
					Factory-lubed and ready to type from day one.
				</li>
				<li>
					<strong>Tri-Mode Connectivity</strong> – Wired USB-C, Bluetooth 5.0, and 2.4GHz wireless. Seamlessly
					switch between up to three devices.
				</li>
				<li>
					<strong>Gasket Mount + Silicone Dampening</strong> – The gasket structure absorbs impact and
					softens the sound profile, giving every keystroke a satisfying, cushioned feel.
				</li>
				<li>
					<strong>Hot-Swappable PCB</strong> – Swap your switches anytime, no soldering needed.
				</li>
				<li>
					<strong>Low-Profile PBT Keycaps</strong> – Durable, shine-resistant, and sculpted for comfortable
					long typing sessions.
				</li>
				<li>
					<strong>Per-Key RGB Lighting</strong> – Dial in the perfect atmosphere with fully customisable
					per-key lighting.
				</li>
				<li>
					<strong>Lightweight &amp; Portable</strong> – At ~680g, the Flow Lite is built to travel. Toss
					it in your bag without a second thought.
				</li>
			</ul>
		</div>
	</section>

	<section class="info-sections">
		<!-- Features -->
		<div class="info-block">
			<h2>Features</h2>
			<ul class="feature-list">
				{#each features as f}
					<li>{f}</li>
				{/each}
			</ul>
		</div>

		<!-- Specs & Details -->
		<div class="info-block">
			<h2>Specs & Details</h2>
			<table class="specs-table">
				{#each specs as s}
					<tr>
						<td class="spec-label">{s.label}</td>
						<td class="spec-value">{s.value}</td>
					</tr>
				{/each}
			</table>
		</div>

		<!-- What's in the Box -->
		<div class="info-block">
			<h2>What's in the Box</h2>
			<ul class="box-list">
				{#each inbox as item}
					<li>{item}</li>
				{/each}
			</ul>
		</div>

		<!-- FAQ -->
		<div class="info-block">
			<h2>FAQ</h2>
			<div class="faq-list">
				{#each faqs as faq, i}
					<div class="faq-item">
						<button
							class="faq-question"
							class:open={openFaq === i}
							onclick={() => (openFaq = openFaq === i ? null : i)}
						>
							{faq.q}
							<span class="faq-icon">{openFaq === i ? '−' : '+'}</span>
						</button>
						{#if openFaq === i}
							<p class="faq-answer" transition:slide>{@html faq.a}</p>
						{/if}
					</div>
				{/each}
			</div>
		</div>
	</section>
</main>

<style>
	.product {
		display: grid;
		grid-template-columns: 1fr 1fr;
		min-height: calc(100vh - 65px);
		overflow: hidden;
	}

	.visual {
		background: #141412;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 1.5rem;
		padding: 4rem;
		border-right: 1px solid #2a2a28;
		min-width: 0;
		overflow: hidden;
		max-width: 100%;
	}
	.main-image {
		width: 420px;
		height: 350px;
		border-radius: 8px;
		overflow: hidden;
	}
	.main-image img,
	.main-image video {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	.thumbnails {
		display: flex;
		gap: 0.6rem;
	}
	.thumb-btn {
		width: 60px;
		height: 50px;
		padding: 0;
		border: 1px solid #3a3a38;
		border-radius: 4px;
		overflow: hidden;
		cursor: pointer;
		opacity: 0.5;
		transition:
			opacity 0.15s,
			border-color 0.15s;
	}
	.thumb-btn img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	.thumb-btn:hover,
	.thumb-btn.active {
		opacity: 1;
		border-color: #f0ede6;
	}
	.thumb-video-wrap {
		position: relative;
		width: 100%;
		height: 100%;
		display: flex;
	}
	.thumb-video-wrap video {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	.play-icon {
		position: absolute;
		inset: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 0.75rem;
		color: #f0ede6;
		background: rgba(0, 0, 0, 0.45);
		pointer-events: none;
	}
	.image-caption {
		font-size: 0.75rem;
		letter-spacing: 0.15em;
		color: #6a6a68;
		text-transform: uppercase;
	}

	.details {
		padding: 4rem 3.5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
		gap: 1.25rem;
		min-width: 0;
		overflow: hidden;
	}
	.collection {
		font-size: 0.75rem;
		letter-spacing: 0.2em;
		color: #8a8a88;
		text-transform: uppercase;
	}
	h1 {
		font-family: 'Playfair Display', serif;
		font-size: 2.8rem;
		line-height: 1.1;
		font-weight: 400;
	}
	.tagline {
		font-size: 1rem;
		color: #a0a09e;
		font-style: italic;
	}
	.price {
		font-size: 1.4rem;
		font-weight: 500;
		letter-spacing: 0.05em;
	}
	.buy-btn {
		display: inline-block;
		background: #f0ede6;
		color: #0e0d0b;
		text-decoration: none;
		padding: 0.85rem 2rem;
		font-size: 0.85rem;
		font-weight: 600;
		letter-spacing: 0.15em;
		text-transform: uppercase;
		border-radius: 2px;
		transition:
			background 0.2s,
			color 0.2s;
		width: fit-content;
	}
	.buy-btn:hover {
		background: #d8d5ce;
	}
	.description {
		font-size: 0.9rem;
		line-height: 1.7;
		color: #b0b0ae;
		border-top: 1px solid #2a2a28;
		padding-top: 1.25rem;
	}

	.perks {
		list-style: none;
		display: flex;
		flex-direction: column;
		gap: 0.4rem;
		border-top: 1px solid #2a2a28;
		padding-top: 1.25rem;
	}
	.perks li {
		font-size: 0.8rem;
		color: #8a8a88;
		letter-spacing: 0.03em;
		line-height: 1.6;
	}
	.perks li strong {
		color: #c0c0be;
		font-weight: 500;
	}

	.info-sections {
		max-width: 860px;
		margin: 0 auto;
		padding: 5rem 3rem;
		width: 100%;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 4rem;
	}

	.info-block h2 {
		font-family: 'Playfair Display', serif;
		font-size: 1.5rem;
		font-weight: 400;
		margin-bottom: 1.5rem;
		padding-bottom: 0.75rem;
		border-bottom: 1px solid #2a2a28;
	}

	.feature-list {
		list-style: none;
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 0.6rem 2rem;
	}
	.feature-list li {
		font-size: 0.875rem;
		color: #b0b0ae;
		line-height: 1.6;
	}
	.feature-list li::before {
		content: '✦ ';
		color: #6a6a68;
		font-size: 0.6rem;
		vertical-align: middle;
	}

	.specs-table {
		width: 100%;
		border-collapse: collapse;
		table-layout: fixed;
		word-break: break-word;
	}
	.specs-table tr {
		border-bottom: 1px solid #1e1e1c;
	}
	.specs-table tr:last-child {
		border-bottom: none;
	}
	.spec-label {
		font-size: 0.8rem;
		color: #6a6a68;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		padding: 0.7rem 0;
		width: 40%;
	}
	.spec-value {
		font-size: 0.875rem;
		color: #d0d0ce;
		padding: 0.7rem 0;
	}

	.box-list {
		list-style: none;
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}
	.box-list li {
		font-size: 0.875rem;
		color: #b0b0ae;
	}
	.box-list li::before {
		content: '— ';
		color: #6a6a68;
	}

	.faq-list {
		display: flex;
		flex-direction: column;
	}
	.faq-item {
		border-bottom: 1px solid #2a2a28;
	}
	.faq-question {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1.1rem 0;
		background: none;
		border: none;
		color: #e0e0de;
		font-size: 0.9rem;
		text-align: left;
		cursor: pointer;
		letter-spacing: 0.02em;
		transition: color 0.15s;
	}
	.faq-question:hover,
	.faq-question.open {
		color: #f0ede6;
	}
	.faq-icon {
		font-size: 1.2rem;
		color: #6a6a68;
		flex-shrink: 0;
		margin-left: 1rem;
	}
	.faq-answer {
		font-size: 0.85rem;
		color: #8a8a88;
		line-height: 1.75;
		padding-bottom: 1.25rem;
		max-width: 680px;
	}
	.faq-answer :global(a) {
		color: #f0ede6;
		text-decoration: underline;
		text-underline-offset: 2px;
	}
	.faq-answer :global(a:hover) {
		color: #d8d5ce;
	}

	@media (max-width: 768px) {
		.product {
			grid-template-columns: 1fr;
		}
		.visual {
			min-height: 40vh;
			border-right: none;
			border-bottom: 1px solid #2a2a28;
		}
		.details {
			padding: 2.5rem 1.5rem;
		}
		h1 {
			font-size: 2rem;
		}
		.info-sections {
			padding: 3rem 1.5rem;
		}
		.feature-list {
			grid-template-columns: 1fr;
		}
	}
</style>
