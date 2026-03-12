<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/ugreen-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = ['/img/ugreen-1.jpg', '/img/ugreen-2.jpg'];

	const product = {
		name: 'UGREEN Ergonomic Wireless Mouse',
		tagline: 'Dual Wireless. Silent Clicks. 300-Day Battery.',
		price: 15,
		description:
			'The UGREEN Ergonomic Wireless Mouse lets you switch instantly between 2.4G and Bluetooth 5.0 — connecting two devices simultaneously with no dongle swaps. A curved grip with UV coating reduces wrist strain, ultra-silent clicks (≤40dB) keep you distraction-free, and a single AA battery lasts up to 300 days with smart 3-stage sleep. Works on virtually any surface, any OS, anywhere.'
	};

	const features = [
		'Dual-mode: Bluetooth 5.0 + 2.4G — 2 devices at once',
		'Ultra-silent clicks ≤40dB — offices, libraries, calls',
		'Curved ergonomic grip with UV coating, reduces wrist strain',
		'5 DPI levels: 800 / 1200 / 1600 / 2400 / 4000',
		'Blue light sensor — tracks on wood, paper, fabric & glass',
		'~300-day battery life (1× AA) with 3-stage smart sleep',
		'5-button layout: left, right, scroll, forward, back',
		'No drivers needed — 15m wireless range, universal OS support'
	];

	const specs = [
		{ label: 'Connectivity', value: 'Bluetooth 5.0 + 2.4G USB Receiver' },
		{ label: 'Multi-device', value: '2 devices simultaneously (BT + 2.4G)' },
		{ label: 'DPI Levels', value: '800 / 1200 / 1600 / 2400 / 4000 (5 levels)' },
		{ label: 'Sensor', value: 'Blue light optical — works on most surfaces' },
		{ label: 'Battery', value: '1× AA, ~300 days (3-stage smart sleep)' },
		{ label: 'Buttons', value: '5 (L, R, scroll, forward, back)' },
		{ label: 'Noise Level', value: '≤40dB ultra-silent clicks' },
		{ label: 'Range', value: 'Up to 15m (unobstructed)' },
		{ label: 'OS Support', value: 'Windows / macOS / Linux / ChromeOS / Android / iPadOS' },
		{ label: 'Condition', value: 'Brand New' }
	];

	const inbox = ['UGREEN Ergonomic Wireless Mouse', '2.4G USB Nano Receiver (pre-stored in mouse)'];

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
			q: 'How do I switch between connected devices?',
			a: 'Press the mode switch button on the mouse to toggle between your 2.4G and Bluetooth connections. Both connections are maintained simultaneously — no re-pairing needed when switching.'
		},
		{
			q: 'Does it work without the USB receiver?',
			a: 'Yes — you can connect via Bluetooth 5.0 without the USB receiver. The 2.4G nano receiver is pre-stored inside the mouse and only needed for 2.4G mode.'
		},
		{
			q: 'Is the AA battery included?',
			a: 'Yes. One standard AA battery lasts approximately 300 days thanks to the 3-stage auto-sleep feature (sleeps after 5s, 10min, and 30min of inactivity).'
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
					<video src={activeMedia} controls autoplay loop />
				{:else}
					<img src={activeMedia} alt="UGREEN Ergonomic Wireless Mouse" />
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
							<video src={item} muted />
						{:else}
							<img src={item} alt="UGREEN Ergonomic Mouse view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">UGREEN Ergonomic Mouse — Dual Wireless, Silent</p>
		</div>

		<div class="details">
			<p class="collection">Ergonomic Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a href="https://www.carousell.sg/" target="_blank" rel="noopener noreferrer" class="buy-btn">
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>Dual-Mode Wireless Freedom</strong> – Switch instantly between 2.4G and Bluetooth 5.0.
					Connect a PC and tablet at the same time — no dongle swaps, no re-pairing.
				</li>
				<li>
					<strong>Ergonomic Grip with UV Coating</strong> – Curved palm shape reduces wrist strain during
					long workdays. Comfortable for extended use in any setting.
				</li>
				<li>
					<strong>Ultra-Silent Clicks (≤40dB)</strong> – Near-inaudible clicks and scroll for distraction-free
					work in libraries, open offices, or video calls.
				</li>
				<li>
					<strong>300-Day Battery Life</strong> – One AA battery lasts up to 300 days. Smart 3-stage
					sleep (5s / 10min / 30min) aggressively cuts power waste when idle.
				</li>
				<li>
					<strong>Blue Light Sensor, Any Surface</strong> – Tracks flawlessly on wood, paper, fabric,
					and glass. 5 DPI levels (800–4000) for precision or speed. 15m wireless range.
				</li>
			</ul>
		</div>
	</section>

	<section class="info-sections">
		<div class="info-block">
			<h2>Features</h2>
			<ul class="feature-list">
				{#each features as f}
					<li>{f}</li>
				{/each}
			</ul>
		</div>

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

		<div class="info-block">
			<h2>What's in the Box</h2>
			<ul class="box-list">
				{#each inbox as item}
					<li>{item}</li>
				{/each}
			</ul>
		</div>

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
	.thumb-btn img,
	.thumb-btn video {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	.thumb-btn:hover,
	.thumb-btn.active {
		opacity: 1;
		border-color: #f0ede6;
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
			padding: 2.5rem 1.5rem;
		}
		.main-image {
			width: 100%;
			height: auto;
			aspect-ratio: 4/3;
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
