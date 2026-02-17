<script>
	const cards = [
		{
			title: 'GamaKay GMK67 Customized Mechanical Keyboard',
			image: '/files/blackpink-keyboard.png',
			link: '/gamakay-gmk67-customized-mechanical-keyboard'
		},
		{
			title: 'Logitech M240 Silent Bluetooth Mouse',
			image: '/files/logitech-m240-silent-bluetooth-mouse.png',
			link: '/logitech-m240-silent-bluetooth-mouse'
		},
		{
			title: 'JBL Tune 770NC Wireless Over-Ear Noise Cancelling Headphones',
			image: '/files/jbl-tune-770nc.png',
			link: '/jbl-tune-770nc-wireless-over-ear-noise-cancelling-headphones'
		},
		{
			title: 'AULA WIN68HE Wireless Mechanical Keyboard',
			image: '/files/aula-win68he.png',
			link: '/aula-win68he-wireless-mechanical-keyboard'
		},
		{
			title: 'AULA F75 Wireless Mechanical Keyboard',
			image: '/files/aula-f75.png',
			link: '/aula-f75-wireless-mechanical-keyboard'
		},
		{
			title: 'Razer Basilisk x Hyperspeed Wireless Gaming Mouse',
			image: '/files/razer-basilisk-x-hyperspeed-wireless-gaming-mouse.png',
			link: '/razer-basilisk-x-hyperspeed-wireless-gaming-mouse'
		}
	];
</script>

<div class="content">
	<div class="card-container">
		{#each cards as card}
			<a class="card" href={card.link}>
				<img src={card.image} alt={card.title} />
				<div class="card-content">
					<div class="card-title">{card.title}</div>
					<button class="card-button">Buy now</button>
				</div>
			</a>
		{/each}
	</div>
</div>

<style lang="scss">
	.content {
		padding-top: 5rem;
		background-color: #fff;
	}

	.card-container {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 1rem;
		padding: 2rem;

		@media (max-width: 768px) {
			grid-template-columns: repeat(2, 1fr);
		}
	}

	.card {
		display: block;
		width: 100%;
		overflow: hidden;
		text-decoration: none;
		color: inherit;
		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease;

		img {
			width: 100%;
			height: 200px;
			object-fit: cover;
			border-radius: 8px;
		}

		@media (max-width: 768px) {
			img {
				height: 150px;
			}
		}
	}

	.card-content {
		padding: 0.5rem 0;
	}

	.card-title {
		font-size: 1.1rem;
		font-weight: 400;
		margin-bottom: 0.5rem;

		@media (max-width: 768px) {
			font-size: 0.9rem;
		}
	}

	.card-button {
		padding: 0.5rem 1rem;
		font-size: 0.95rem;
		background: transparent;
		border: 2px solid #333;
		border-radius: 50px;
		color: #333;
		cursor: pointer;
		transition: all 0.2s ease;
		display: inline-block;
	}

	.card-button:hover {
		background: #333;
		color: #fff;
	}

	@media (max-width: 768px) {
		.card-button {
			font-size: 0.85rem;
			padding: 0.4rem 0.8rem;
		}
	}
</style>
