<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/linky87-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = [
		'/img/linky87-1.jpg',
		'/img/linky87-2.jpg',
		'/img/linky87-3.jpg',
		'/img/linky87-4.jpg',
		'/img/linky87-5.jpg',
		'/img/linky87-6.jpg',
		'/img/linky87.MP4'
	];

	const product = {
		name: 'Elecfox Linky 87 TKL Mechanical Keyboard',
		tagline: 'Gasket Mounted. Tri-Mode Wireless. Timber Green.',
		price: 70,
		description:
			'The Elecfox Linky 87 is a premium TKL mechanical keyboard that punches well above its price. Gasket-mounted with Rogers filling foam, pre-lubed BSUN TaiChi linear switches, and double-shot PBT keycaps — it delivers a deep, creamy thock out of the box. Connect via Bluetooth 5.0, 2.4GHz, or USB-C, and customise everything through VIA without installing a single app. Timber Green colourway.'
	};

	const features = [
		'Gasket-mounted with Rogers filling foam for HiFi sound',
		'Pre-lubed BSUN TaiChi linear switches — smooth & satisfying',
		'Tri-mode: Bluetooth 5.0 / 2.4GHz / USB-C wired',
		'Pairs with up to 5 Bluetooth devices simultaneously',
		'Hot-swappable PCB — 3-pin & 5-pin, no soldering needed',
		'Double-shot PBT keycaps — fade-resistant, durable legends',
		'Per-key RGB + side glow + backlit logo, 40 lighting modes',
		'VIA compatible — remap keys & macros in-browser, no software',
		'N-key rollover — every keypress registered, no ghosting',
		'4000mAh built-in battery — long wireless sessions',
		'Adjustable dual-stage footrest',
		'Includes keycap puller & switch puller'
	];

	const specs = [
		{ label: 'Layout', value: '87-key Tenkeyless (TKL)' },
		{ label: 'Colour', value: 'Timber Green' },
		{ label: 'Switches', value: 'Pre-lubed BSUN TaiChi Linear (hot-swappable)' },
		{ label: 'Keycaps', value: 'Double-shot PBT' },
		{ label: 'Connectivity', value: 'Bluetooth 5.0 / 2.4GHz wireless / USB-C wired' },
		{ label: 'Bluetooth Devices', value: 'Up to 5 paired devices' },
		{ label: 'Latency', value: 'Wired 2.71ms · 2.4GHz 4.98ms · BT 11.99ms' },
		{ label: 'Battery', value: '4000mAh built-in rechargeable' },
		{ label: 'Key Travel', value: '3.6mm' },
		{ label: 'Actuation Force', value: '40g' },
		{ label: 'Key Lifespan', value: '50 million keystrokes' },
		{ label: 'Lighting', value: 'Per-key RGB + side RGB + logo, 40 modes, 16.8M colours' },
		{ label: 'Customisation', value: 'VIA (browser-based, no install needed)' },
		{ label: 'PCB', value: 'Hot-swap, 3-pin & 5-pin compatible' },
		{ label: 'Structure', value: 'Gasket-mounted + Rogers filling foam + 8× IXPE switch pad' },
		{ label: 'OS Support', value: 'Windows 7/8/10/11 · macOS · iOS · Android' },
		{ label: 'Weight', value: 'Approx. 1050g' },
		{ label: 'Condition', value: 'Brand New' }
	];

	const inbox = [
		'Elecfox Linky 87 TKL Keyboard (Timber Green)',
		'2.4GHz USB Nano Receiver (pre-stored in keyboard)',
		'USB-C charging / data cable',
		'Keycap puller',
		'Switch puller'
	];

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
			q: 'How do I request a return or refund?',
			a: "Just tap on 'Return/refund' on your order details page if something goes wrong with your order. Carousell will reach out to you via email within 24h to resolve the issue.<br><a href='https://support.carousell.com/hc/en-us/articles/360001548627--Singapore-How-do-I-raise-a-return-refund-request' target='_blank' rel='noopener noreferrer'>Learn more</a>"
		},
		{
			q: 'How do I switch between Bluetooth devices?',
			a: 'Press and hold FN + Q/W/E/R/T for 3–5 seconds to pair up to 5 Bluetooth channels. To switch between paired devices, press the corresponding FN + key combination briefly.'
		},
		{
			q: 'How do I connect via 2.4GHz?',
			a: 'The nano USB receiver is pre-stored inside the keyboard. Plug it into your computer, set the mode switch to 2.4GHz, and it connects automatically — no pairing needed.'
		},
		{
			q: 'Does it work wired?',
			a: 'Yes. Connect the included USB-C cable and the keyboard switches to wired mode automatically. It also charges the battery while in wired mode.'
		},
		{
			q: 'Can I swap the switches?',
			a: 'Yes — the PCB is fully hot-swappable and supports both 3-pin and 5-pin switches. No soldering required. Use the included switch puller to swap them out.'
		},
		{
			q: 'How do I customise the lighting and keybinds?',
			a: 'The Linky 87 is VIA compatible. Go to usevia.app in your browser, connect the keyboard via USB-C, and you can remap keys, create macros, and fine-tune RGB — no software to install.'
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
					<video src={activeMedia} controls autoplay loop poster="/img/linky87-video-thumb.png" />
				{:else}
					<img src={activeMedia} alt="Elecfox Linky 87 Timber Green" />
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
							<img src={item} alt="Linky 87 view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">Elecfox Linky 87 — Timber Green</p>
		</div>

		<div class="details">
			<p class="collection">Linky Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a
				href="https://www.carousell.sg/p/creamy-elecfox-linky-87-tkl-customised-mechanical-keyboard-1436950421/?referrer_source=me_page"
				target="_blank"
				rel="noopener noreferrer"
				class="buy-btn"
			>
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>Gasket-Mounted + Rogers Foam</strong> – A construction usually reserved for boards
					3–5× the price. Deep, dampened thock with no case rattle.
				</li>
				<li>
					<strong>Pre-Lubed Linear Switches</strong> – BSUN TaiChi linears come smooth and satisfying
					straight out of the box. Hot-swappable for when you want to experiment.
				</li>
				<li>
					<strong>Tri-Mode Wireless</strong> – Bluetooth 5.0, 2.4GHz, and USB-C wired. Pair up to 5 Bluetooth
					devices and switch between them instantly.
				</li>
				<li>
					<strong>VIA Customisation</strong> – Remap every key, set macros, and dial in your RGB from
					the browser. No apps, no drivers, no friction.
				</li>
				<li>
					<strong>4000mAh Battery + Double-Shot PBT</strong> – A big battery for long wireless sessions,
					and keycaps built to last with fade-resistant legends.
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
