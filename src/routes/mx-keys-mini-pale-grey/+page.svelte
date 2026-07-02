<script>
	import { slide } from 'svelte/transition';

	let activeMedia = $state('/img/mxkeys-white-1.jpg');
	let isVideo = $derived(activeMedia.endsWith('.MP4'));

	const media = [
		'/img/mxkeys-white-1.jpg',
		'/img/mxkeys-white-2.jpg',
		'/img/mxkeys-white-3.jpg',
		'/img/mxkeys-white-4.jpg'
	];

	const product = {
		name: 'Logitech MX Keys Mini - Pale Grey',
		tagline: 'Compact by design. Comfortable by feel. Pale Grey.',
		price: 100,
		description:
			'The Logitech MX Keys Mini brings all the comfort of the full-size MX Keys into a compact 75% frame. Low-profile, concave keycaps and Perfect Stroke keys give every keypress a quiet, stable feel, while smart backlighting adjusts automatically as your hands approach. Pair up to 3 devices over Bluetooth and switch between them instantly with Easy-Switch. Pale Grey colourway.'
	};

	const features = [
		'Compact 75% layout — closer reach to your mouse, no numpad',
		'Low-profile, concave spherical keycaps for stable typing',
		'Perfect Stroke keys — quiet, precise 1.5mm actuation',
		'Smart illumination — backlights adjust as your hands approach',
		'Easy-Switch — pair up to 3 devices, switch instantly',
		'Bluetooth Low Energy or Logi Bolt USB receiver connectivity',
		'USB-C rechargeable — up to 10 days with backlight on',
		'Up to 5 months battery life with backlight off',
		'Works across Windows, macOS, Linux, iOS, Android, ChromeOS',
		'Customisable via Logi Options+ software',
		'Spill-resistant design',
		'Matte coating resists fingerprints and smudges'
	];

	const specs = [
		{ label: 'Layout', value: 'Compact 75% (no numpad)' },
		{ label: 'Colour', value: 'Pale Grey' },
		{ label: 'Keys', value: 'Perfect Stroke low-profile scissor keys' },
		{ label: 'Keycaps', value: 'Low-profile, concave, matte coated' },
		{ label: 'Connectivity', value: 'Bluetooth Low Energy / Logi Bolt USB receiver' },
		{ label: 'Paired Devices', value: 'Up to 3, via Easy-Switch button' },
		{ label: 'Battery', value: 'Built-in rechargeable Li-Po' },
		{ label: 'Battery Life', value: 'Up to 10 days (backlight on) / 5 months (off)' },
		{ label: 'Charging', value: 'USB-C' },
		{ label: 'Backlighting', value: 'White LED, auto on/off via proximity sensor' },
		{ label: 'Software', value: 'Logi Options+ (optional)' },
		{ label: 'OS Support', value: 'Windows 10/11 · macOS · Linux · iOS · Android · ChromeOS' },
		{ label: 'Weight', value: 'Approx. 506g' },
		{ label: 'Condition', value: 'Brand New' }
	];

	const inbox = [
		'Logitech MX Keys Mini Keyboard (Pale Grey)',
		'Logi Bolt USB Receiver',
		'USB-C charging cable',
		'Quick start guide'
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
			q: 'How do I switch between paired devices?',
			a: 'Press the Easy-Switch button on the keyboard corresponding to the device slot (1, 2, or 3) you paired it to. The keyboard reconnects instantly.'
		},
		{
			q: 'How do I pair a new device?',
			a: "Hold the Easy-Switch button for a device slot for 3 seconds until the LED blinks, then select the keyboard from your device's Bluetooth settings."
		},
		{
			q: 'Does it come with a USB receiver?',
			a: 'Yes — a Logi Bolt USB receiver is included in the box, in addition to Bluetooth connectivity.'
		},
		{
			q: 'How long does the battery last?',
			a: 'Up to 10 days on a full charge with backlighting on, or up to 5 months with backlighting off. Charges via USB-C.'
		},
		{
			q: 'Can I customise the keys?',
			a: "Yes, using Logitech's free Logi Options+ software you can remap keys and adjust backlighting behaviour on Windows or macOS."
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
						poster="/img/mxkeys-white-video-thumb.png"
					/>
				{:else}
					<img src={activeMedia} alt="Logitech MX Keys Mini Pale Grey" />
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
							<img src={item} alt="MX Keys Mini view" />
						{/if}
					</button>
				{/each}
			</div>
			<p class="image-caption">Logitech MX Keys Mini — Pale Grey</p>
		</div>

		<div class="details">
			<p class="collection">MX Series</p>
			<h1>{product.name}</h1>
			<p class="tagline">{product.tagline}</p>
			<p class="price">${product.price} SGD</p>
			<a
				href="https://www.carousell.sg/p/logitech-mx-keys-mini-wireless-low-profile-keyboard-1446444523/?t-id=DKpYKLlX5V_1780729958132&t-referrer_browse_type=seller&t-referrer_page_type=profile&t-referrer_request_id=k7auHBK3kWBVk_8Z&t-tap_index=4"
				target="_blank"
				rel="noopener noreferrer"
				class="buy-btn"
			>
				Buy Now
			</a>
			<p class="description">{product.description}</p>

			<ul class="perks">
				<li>
					<strong>Compact 75% Layout</strong> – No numpad means your mouse sits closer, easier on the
					shoulder for everyday typing.
				</li>
				<li>
					<strong>Perfect Stroke Keys</strong> – Low-profile, concave keycaps give a quiet, stable, satisfying
					typing feel out of the box.
				</li>
				<li>
					<strong>Easy-Switch, 3 Devices</strong> – Pair a laptop, tablet, and phone, and jump between
					them with one button press.
				</li>
				<li>
					<strong>Smart Backlighting</strong> – Keys light up automatically as your hands approach, and
					dim when you step away to save battery.
				</li>
				<li>
					<strong>USB-C Fast Charging</strong> – Up to 10 days per charge with backlight on, up to 5
					months with it off.
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
