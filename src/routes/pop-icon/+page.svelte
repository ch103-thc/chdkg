<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/pop-icon-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = [
		'/img/pop-icon-1.jpg',
		'/img/pop-icon-2.jpg',
		'/img/pop-icon-3.jpg',
		'/img/pop-icon-4.jpg',
		'/img/pop-icon.MP4'
	];

	const product = {
		name: 'Logitech POP Icon Keys',
		tagline: 'Bold looks. Effortless typing.',
		price: 60,
		description:
			'The Logitech POP Icon Keys is a compact wireless Bluetooth keyboard with a detailed transparent frame and bold colourway made from recycled plastic. Contoured, low-profile keys give a quiet, comfortable typing feel, and customizable Action Keys let you launch shortcuts, emoji, or AI tools in a tap.'
	};

	const features = [
		'Customizable Action Keys via Logi Options+ app',
		'Contoured, low-profile keys for quiet, comfortable typing',
		'Bluetooth Low Energy — pairs with up to 3 devices',
		'Easy-Switch button to jump between paired devices',
		'Compact layout — saves desk space',
		'Up to 3-year battery life on 2× AAA batteries (included)',
		'Made with recycled plastic, transparent detail frame',
		'Multi-OS: Windows, macOS, ChromeOS, Linux, iOS, iPadOS, Android'
	];

	const specs = [
		{ label: 'Layout', value: 'Compact' },
		{ label: 'Switch Type', value: 'Low-profile membrane' },
		{ label: 'Battery', value: '2× AAA (included, up to 3 yrs)' },
		{ label: 'Connectivity', value: 'Bluetooth Low Energy' },
		{ label: 'Devices Paired', value: 'Up to 3, Easy-Switch' },
		{ label: 'Dimensions', value: '12.78" x 12.78" x 0.87"' },
		{ label: 'Weight', value: '~1.17 lb' },
		{ label: 'Colour', value: 'Off White & Orange' }
	];

	const inbox = [
		'Logitech POP Icon Keys Keyboard',
		'2× AAA Batteries (pre-installed)',
		'Quick Start Guide',
		'Warranty Card'
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
			q: 'Can I customize the Action Keys?',
			a: 'Yes — download the Logi Options+ app to remap the Action Keys to shortcuts, emoji, or app launches.'
		},
		{
			q: 'How long does the battery last?',
			a: 'Logitech rates it for up to 3 years on the included AAA batteries, with auto-sleep to save power when idle.'
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
					<video src={activeMedia} controls autoplay loop poster="/img/logitech-pop-icon-video-thumb.png" />
				{:else}
					<img src={activeMedia} alt="Logitech POP Icon Keys" />
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
							<img src={item} alt="Logitech POP Icon Keys view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">Logitech POP Icon Keys — Off White & Orange</p>
		</div>

		<div class="details">
			<p class="collection">F Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a
				href="https://www.carousell.sg/p/logitech-pop-icon-keys-wireless-mechanical-keyboard-1462943643/"
				target="_blank"
				rel="noopener noreferrer"
				class="buy-btn"
			>
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>Compact Layout</strong> – A space-saving footprint that frees up desk room without
					sacrificing a full set of keys.
				</li>
				<li>
					<strong>Customizable Action Keys</strong> – Remap shortcuts, emoji, or app launches through
					the Logi Options+ app to match how you work.
				</li>
				<li>
					<strong>Bluetooth Low Energy</strong> – Pair with up to 3 devices and jump between them instantly
					with the Easy-Switch button.
				</li>
				<li>
					<strong>Up to 3-Year Battery Life</strong> – Runs on 2× included AAA batteries with auto-sleep
					power saving, so you're not chasing a charging cable.
				</li>
				<li>
					<strong>Low-Profile, Contoured Keys</strong> – Shaped to fit your fingertips for a quiet, comfortable,
					laptop-like typing feel.
				</li>
				<li>
					<strong>Recycled Plastic Build</strong> – Made with a meaningful share of post-consumer recycled
					plastic, varying by colourway.
				</li>
				<li>
					<strong>Multi-OS Compatible</strong> – Works across Windows, macOS, ChromeOS, Linux, iOS/iPadOS,
					and Android.
				</li>
				<li>
					<strong>Off White & Orange Colourway</strong> – A bold two-tone finish with a transparent detail
					frame that stands out on any desk.
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
	@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@300;400;500;600&display=swap');

	:global(body) {
		background: #fafafa;
		color: #1a1a1a;
		font-family: 'Inter', sans-serif;
		-webkit-font-smoothing: antialiased;
	}

	.product {
		display: grid;
		grid-template-columns: 1fr 1fr;
		min-height: calc(100vh - 65px);
		overflow: hidden;
	}

	.visual {
		background: #f5f5f7;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 1.5rem;
		padding: 4rem;
		border-right: 1px solid #ececec;
		min-width: 0;
		overflow: hidden;
		max-width: 100%;
	}
	.main-image {
		width: 420px;
		height: 350px;
		border-radius: 14px;
		overflow: hidden;
		background: #fff;
		border: 1px solid #ececec;
		box-shadow: 0 1px 2px rgba(0, 0, 0, 0.02);
	}
	.main-image img {
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
		border: 1px solid #ececec;
		border-radius: 8px;
		overflow: hidden;
		cursor: pointer;
		background: #fff;
		opacity: 0.6;
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
		border-color: #6366f1;
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
		color: #fff;
		background: rgba(0, 0, 0, 0.35);
		pointer-events: none;
	}
	.image-caption {
		font-size: 0.7rem;
		letter-spacing: 0.18em;
		color: #a0a0a0;
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
		font-size: 0.7rem;
		letter-spacing: 0.25em;
		color: #a0a0a0;
		text-transform: uppercase;
	}
	h1 {
		font-family: 'Space Grotesk', sans-serif;
		font-size: 2.8rem;
		line-height: 1.1;
		font-weight: 600;
		color: #1a1a1a;
	}
	.tagline {
		font-size: 1rem;
		color: #7a7a7a;
		font-style: normal;
	}
	.price {
		font-size: 1.4rem;
		font-weight: 500;
		letter-spacing: 0.04em;
		color: #1a1a1a;
	}
	.buy-btn {
		display: inline-block;
		background: #1a1a1a;
		color: #fff;
		text-decoration: none;
		padding: 0.85rem 2rem;
		font-size: 0.78rem;
		font-weight: 600;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		border-radius: 2px;
		transition: background 0.2s;
		width: fit-content;
	}
	.buy-btn:hover {
		background: #6366f1;
	}
	.description {
		font-size: 0.9rem;
		line-height: 1.7;
		color: #6a6a6a;
		border-top: 1px solid #f0f0f0;
		padding-top: 1.25rem;
	}
	.perks {
		list-style: none;
		display: flex;
		flex-direction: column;
		gap: 0.4rem;
		border-top: 1px solid #f0f0f0;
		padding-top: 1.25rem;
	}
	.perks li {
		font-size: 0.8rem;
		color: #7a7a7a;
		letter-spacing: 0.02em;
		line-height: 1.6;
	}
	.perks li strong {
		color: #1a1a1a;
		font-weight: 500;
	}
	/* .perks li::before {
		content: '— ';
	} */

	.info-sections {
		max-width: 860px;
		margin: 0 auto;
		padding: 4rem 3rem;
		width: 100%;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}
	.info-block {
		background: #fff;
		border: 1px solid #ececec;
		border-radius: 14px;
		padding: 2rem;
		box-shadow: 0 1px 2px rgba(0, 0, 0, 0.02);
	}
	.info-block h2 {
		font-family: 'Space Grotesk', sans-serif;
		font-size: 1.3rem;
		font-weight: 600;
		color: #1a1a1a;
		margin-bottom: 1.25rem;
		padding-bottom: 0.75rem;
		border-bottom: 1px solid #f0f0f0;
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
		color: #4a4a4a;
		line-height: 1.6;
	}
	.feature-list li::before {
		content: '✦ ';
		color: #6366f1;
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
		border-bottom: 1px solid #f0f0f0;
	}
	.spec-label {
		font-size: 0.75rem;
		color: #8a8a8a;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		padding: 0.7rem 0;
		width: 40%;
	}
	.spec-value {
		font-size: 0.875rem;
		color: #1a1a1a;
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
		color: #4a4a4a;
	}
	.box-list li::before {
		content: '— ';
		color: #a0a0a0;
	}

	/* FAQ */
	.faq-list {
		display: flex;
		flex-direction: column;
	}
	.faq-item {
		border-bottom: 1px solid #f0f0f0;
	}
	.faq-question {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1.1rem 0;
		background: none;
		border: none;
		color: #1a1a1a;
		font-family: 'Inter', sans-serif;
		font-size: 0.9rem;
		text-align: left;
		cursor: pointer;
		transition: color 0.15s;
	}
	.faq-question:hover,
	.faq-question.open {
		color: #6366f1;
	}
	.faq-icon {
		font-size: 1.2rem;
		color: #a0a0a0;
		flex-shrink: 0;
		margin-left: 1rem;
	}
	.faq-answer {
		font-size: 0.85rem;
		color: #6a6a6a;
		line-height: 1.75;
		padding-bottom: 1.25rem;
		max-width: 680px;
	}
	.faq-answer :global(a) {
		color: #6366f1;
		text-decoration: underline;
		text-underline-offset: 2px;
	}
	.faq-answer :global(a:hover) {
		color: #4f46e5;
	}

	@media (max-width: 768px) {
		.product {
			grid-template-columns: 1fr;
		}
		.visual {
			border-bottom: 1px solid #ececec;
		}
		.main-image {
			width: 100%;
			max-width: 420px;
		}
		.info-block {
			padding: 1.5rem;
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
