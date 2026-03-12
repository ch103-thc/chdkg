<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/logitech-m650-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = ['/img/logitech-m650-1.jpg', '/img/logitech-m650-2.jpg'];

	const product = {
		name: 'Logitech Signature M650',
		tagline: 'Smart Scroll. Silent Clicks. Shaped for You.',
		price: 44,
		description:
			'The Logitech Signature M650 is an ergonomic wireless mouse built for all-day comfort. Featuring SmartWheel scrolling that switches instantly between line-by-line precision and free-spin speed, SilentTouch technology for 90% quieter clicks, and a 24-month battery life — it connects via Bluetooth or Logi Bolt for a seamless, clutter-free setup.'
	};

	const features = [
		'90% quieter clicks with SilentTouch technology',
		'SmartWheel — line-by-line or free-spin scrolling',
		'Bluetooth Low Energy + Logi Bolt USB receiver',
		'Up to 24 months on a single AA battery',
		'400-4000 DPI optical sensor for smooth tracking',
		'Contoured shape with soft thumb area & rubber grips',
		'2 customizable side buttons via Logi Options+',
		'Compatible with Windows, macOS, ChromeOS, Linux, iPadOS, Android'
	];

	const specs = [
		{ label: 'Connectivity', value: 'Bluetooth LE + Logi Bolt USB' },
		{ label: 'DPI', value: '400-4000 DPI optical sensor' },
		{ label: 'Battery', value: '1× AA (~24 months)' },
		{ label: 'Buttons', value: '5 (L, R, scroll click, 2× side)' },
		{ label: 'Design', value: 'Right-handed ergonomic' },
		{ label: 'Scroll', value: 'SmartWheel (precision + free-spin)' },
		{ label: 'OS Support', value: 'Windows / macOS / ChromeOS / Linux / iPadOS / Android' },
		{ label: 'Condition', value: 'Brand New' }
	];

	const inbox = [
		'Logitech Signature M650 Wireless Mouse',
		'Logi Bolt USB Receiver',
		'1× AA Battery (pre-installed)'
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
			q: 'How do I request for a return or refund?',
			a: "Just tap on 'Return/refund' on your order details page if something goes wrong with your order. Carousell will reach out to you via email within 24h to resolve the issue.<br><a href='https://support.carousell.com/hc/en-us/articles/360001548627--Singapore-How-do-I-raise-a-return-refund-request' target='_blank' rel='noopener noreferrer'>Learn more</a>"
		},
		{
			q: 'What is SmartWheel scrolling?',
			a: 'SmartWheel automatically switches between two modes: precise line-by-line scrolling for detailed work, and free-spin mode for rapidly moving through long pages — all with a single flick of your finger.'
		},
		{
			q: 'Does it work without the USB receiver?',
			a: 'Yes — it connects via Bluetooth Low Energy directly to your device without needing the Logi Bolt USB receiver. The receiver is included as an alternative connection option.'
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
					<img src={activeMedia} alt="Logitech Signature M650" />
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
							<img src={item} alt="Logitech Signature M650 view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">Logitech Signature M650 — Silent Wireless Mouse</p>
		</div>

		<div class="details">
			<p class="collection">Signature Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a
				href="https://www.carousell.sg/p/logitech-signature-m650-wireless-mouse-1414576336/"
				target="_blank"
				rel="noopener noreferrer"
				class="buy-btn"
			>
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>SmartWheel Scrolling</strong> – Instantly switch between line-by-line precision for
					documents and free-spin speed for long pages — all with a flick of your finger.
				</li>
				<li>
					<strong>SilentTouch Technology</strong> – Up to 90% quieter clicks than standard mice. Stay
					focused in shared spaces, libraries, or video calls.
				</li>
				<li>
					<strong>Bluetooth + Logi Bolt</strong> – Two ways to connect. Plug-free Bluetooth or the included
					Logi Bolt USB receiver for a rock-solid wireless link up to 10m.
				</li>
				<li>
					<strong>24-Month Battery Life</strong> – One AA battery powers up to two years of work. Less
					time hunting for batteries, more time getting things done.
				</li>
				<li>
					<strong>Ergonomic Comfort Design</strong> – Contoured shape, soft thumb area, and rubber side
					grips crafted for small-to-medium right hands. Built for long sessions.
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

	/* Features */
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

	/* Specs */
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

	/* In the Box */
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

	/* FAQ */
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
