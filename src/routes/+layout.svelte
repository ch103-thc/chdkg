<script>
	import Icon from '@iconify/svelte';
	import '@fontsource/poppins';
	import { onMount } from 'svelte';
	import favicon from '$lib/assets/favicon.jpg';
	let { children } = $props();

	let isMenuOpen = $state(false);
	let isMobile = $state(false);
	let isDropdownOpen = $state(false);

	const checkMobile = () => {
		isMobile = window.innerWidth <= 768;
	};

	const toggleMenu = () => {
		isMenuOpen = !isMenuOpen;
	};

	const handleClickOutside = (e) => {
		if (isMenuOpen && !e.target.closest('.menulist') && !e.target.closest('.menu-toggle')) {
			isMenuOpen = false;
		}
		if (isDropdownOpen && !e.target.closest('.dropdown')) {
			isDropdownOpen = false;
		}
	};

	onMount(() => {
		checkMobile();
		window.addEventListener('resize', checkMobile);
		document.addEventListener('click', handleClickOutside);

		return () => {
			window.removeEventListener('resize', checkMobile);
			document.removeEventListener('click', handleClickOutside);
		};
	});
</script>

<svelte:window on:resize={checkMobile} />

<main>
	<div class="nav">
		<div class="logo">
			<a href="/" class="logo-link">
				<img src={favicon} alt="Logo" class="logo-img" />
				<h1 class="username">chdkg</h1>
			</a>
		</div>

		<button class="menu-toggle" onclick={toggleMenu}>
			<Icon icon={isMenuOpen ? 'mdi:close' : 'mdi:menu'} width="24" height="24" />
		</button>

		<ul class="menulist" class:active={isMenuOpen}>
			<!-- Desktop dropdown trigger -->
			<li class="dropdown" class:open={isDropdownOpen}>
				<button class="dropdown-trigger" onclick={() => (isDropdownOpen = !isDropdownOpen)}>
					Menu <Icon icon="mdi:chevron-down" width="18" height="18" />
				</button>
				<ul class="dropdown-menu">
					<li><a href="/gamakay-gmk67-customized-mechanical-keyboard">GMK67</a></li>
					<li><a href="/logitech-m240-silent-bluetooth-mouse">Logitech M240</a></li>
					<li>
						<a href="/jbl-tune-770nc-wireless-over-ear-noise-cancelling-headphones"
							>JBL Tune 770NC</a
						>
					</li>
					<li><a href="/aula-win68he-wireless-mechanical-keyboard">AULA WIN68HE</a></li>
					<li><a href="/aula-f75-wireless-mechanical-keyboard">AULA F75</a></li>
					<li>
						<a href="/razer-basilisk-x-hyperspeed-wireless-gaming-mouse"
							>Razer Basilisk x Hyperspeed</a
						>
					</li>
				</ul>
			</li>

			<!-- Mobile links (unchanged) -->
			{#if isMobile}
				<li>
					<a href="/gamakay-gmk67-customized-mechanical-keyboard" onclick={toggleMenu}
						>GMK67 <Icon icon="ep:right" width="20" height="20" class="menu-icon" /></a
					>
				</li>
				<li>
					<a href="/logitech-m240-silent-bluetooth-mouse" onclick={toggleMenu}
						>Logitech M240 <Icon icon="ep:right" width="20" height="20" class="menu-icon" /></a
					>
				</li>
				<li>
					<a
						href="/jbl-tune-770nc-wireless-over-ear-noise-cancelling-headphones"
						onclick={toggleMenu}
						>JBL Tune 770NC <Icon icon="ep:right" width="20" height="20" class="menu-icon" /></a
					>
				</li>
				<li>
					<a href="/aula-win68he-wireless-mechanical-keyboard" onclick={toggleMenu}
						>AULA WIN68HE <Icon icon="ep:right" width="20" height="20" class="menu-icon" /></a
					>
				</li>
				<li>
					<a href="/aula-f75-wireless-mechanical-keyboard" onclick={toggleMenu}
						>AULA F75 <Icon icon="ep:right" width="20" height="20" class="menu-icon" /></a
					>
				</li>
				<li>
					<a href="/razer-basilisk-x-hyperspeed-wireless-gaming-mouse" onclick={toggleMenu}
						>Razer Basilisk x Hyperspeed <Icon
							icon="ep:right"
							width="20"
							height="20"
							class="menu-icon"
						/></a
					>
				</li>
			{/if}

			<li class="social-links">
				<a href="https://www.instagram.com/swiftcurated" target="_blank" rel="noopener">
					<Icon icon="mdi:instagram" width="20" height="20" />
				</a>
			</li>
		</ul>
	</div>

	{@render children()}

	<footer class="footer">
		<div class="footer-content">
			<p>
				&copy; {new Date().getFullYear()} chdkg. All rights reserved.
			</p>
		</div>
	</footer>
</main>

<style lang="scss">
	main {
		font-family: 'Poppins', sans-serif;
	}

	.nav {
		position: fixed;
		top: 0;
		right: 0;
		padding: 0.5rem 1.5rem;
		width: 100%;
		z-index: 1000;
		display: flex;
		align-items: center;
		justify-content: space-between;
		transition: all 0.6s ease;
		background: rgba(255, 255, 255, 0.4);
		backdrop-filter: blur(10px);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		height: 80px;

		.logo {
			display: flex;
			align-items: center;

			.logo-link {
				display: flex;
				align-items: center;
				text-decoration: none;

				.logo-img {
					width: 50px;
					height: 50px;
					border-radius: 50%;
					object-fit: cover;
					margin-right: 10px;
					margin-left: 50px;
				}
			}

			.username {
				color: black;
				font-weight: bold;
				font-size: 1rem;
			}
		}

		.menu-toggle {
			display: none;
			background: none;
			border: none;
			cursor: pointer;
			padding: 5px;
			z-index: 1001;
		}

		.menulist {
			display: flex;
			list-style: none;
			margin: 0;
			padding: 0;
			gap: 10px;

			li {
				a {
					display: flex;
					align-items: center;
					text-decoration: none;
					color: inherit;
					padding: 8px 16px;

					.menu-icon {
						margin-left: 10px;
						flex-shrink: 0;
					}
				}
			}

			&.active {
				right: 0;
			}

			.social-links {
				display: none;

				@media (max-width: 768px) {
					display: flex;
					justify-content: center;
					width: 100%;
					margin-top: auto;
					padding: 1rem 0;
					border-top: 1px solid rgba(0, 0, 0, 0.1);
				}

				a {
					color: inherit;
				}
			}
		}

		.dropdown {
			position: relative;

			.dropdown-trigger {
				display: flex;
				align-items: center;
				gap: 4px;
				background: none;
				border: none;
				cursor: pointer;
				font-family: 'Poppins', sans-serif;
				font-size: 1rem;
				padding: 8px 16px;
			}

			.dropdown-menu {
				display: none;
				position: absolute;
				top: calc(100% + 8px);
				right: 0;
				background: white;
				border: 1px solid rgba(0, 0, 0, 0.1);
				border-radius: 8px;
				list-style: none;
				padding: 8px 0;
				margin: 0;
				min-width: 220px;
				box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);

				li a {
					padding: 10px 20px;
					white-space: nowrap;
					display: block;

					&:hover {
						background: rgba(0, 0, 0, 0.04);
					}
				}
			}

			&.open .dropdown-menu {
				display: block;
			}

			@media (max-width: 768px) {
				display: none;
			}
		}

		@media (max-width: 768px) {
			padding: 15px 5%;

			.menu-toggle {
				display: block;
			}

			.menulist {
				position: fixed;
				top: 0px;
				right: -100%;
				width: 70%;
				height: 100vh;
				background: white;
				backdrop-filter: blur(10px);
				flex-direction: column;
				align-items: flex-start;
				justify-content: flex-start;
				transition: all 0.5s ease;
				padding: 30px 0;
				gap: 10px;
				z-index: 999;
				border-left: 1px solid rgba(0, 0, 0, 0.1);

				li {
					width: 100%;
					padding: 5px 10px;

					a {
						display: flex;
						align-items: center;
						justify-content: space-between;
						width: 100%;
						padding: 6px 1.5rem;
					}
				}
			}
		}

		@media (max-width: 480px) {
			.logo {
				.logo-link {
					.logo-img {
						width: 40px;
						height: 40px;
					}
				}

				.username {
					font-size: 0.9rem;
				}
			}

			.menulist {
				width: 80%;
			}
		}
	}

	.footer {
		padding: 1rem;
		text-align: center;

		.footer-content {
			display: flex;
			justify-content: center;
			align-items: center;
			max-width: 1200px;
			margin: 0 auto;
		}

		@media (max-width: 768px) {
			padding: 5px;

			p {
				font-size: 0.9rem;
			}
		}
	}
</style>
