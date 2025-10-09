<script>
    const cards = [
        {
            title: "Blackpink GamaKay GMK67 Customized Mechanical Keyboard",
            label: "Order a GMK67",
            image: "/files/blackpink-keyboard.png",
            link: "/blackpink-gamakay-gmk67-customized-mechanical-keyboard",
        },
        {
            title: "Logitech M240 Silent Bluetooth Mouse",
            label: "Order a Logitech M240",
            image: "/files/logitech-m240-silent-bluetooth-mouse.png",
            link: "/logitech-m240-silent-bluetooth-mouse",
        },
        {
            title: "JBL Tune 770NC Wireless Over-Ear Noise Cancelling Headphones",
            label: "Order a JBL Tune 770NC",
            image: "/files/jbl-tune-770nc.png",
            link: "/jbl-tune-770nc-wireless-over-ear-noise-cancelling-headphones",
        },
        {
            title: "Logitech MX Keys Mini Wireless Keyboard",
            label: "Order a Logitech MX Keys Mini",
            image: "/files/logitech-mx-keys-mini-wireless-keyboard.png",
            link: "/logitech-mx-keys-mini-wireless-keyboard",
        },
        {
            title: "Razer Basilisk x Hyperspeed Wireless Gaming Mouse",
            label: "Order a Razer Basilisk x Hyperspeed",
            image: "/files/razer-basilisk-x-hyperspeed-wireless-gaming-mouse.png",
            link: "/razer-basilisk-x-hyperspeed-wireless-gaming-mouse",
        },
    ];
</script>

<div class="content">
    <div class="card-container">
        {#each cards as card}
            <a class="card" href={card.link}>
                <img src={card.image} alt={card.title} />
                <div class="card-title">
                    {card.title}
                    <div class="card-label">{card.label}</div>
                </div>
            </a>
        {/each}
    </div>
</div>

<style lang="scss">
    .content {
        padding-top: 5rem;
        background-color: #f0f4f8;
    }

    .card-container {
        display: flex;
        gap: 1rem;
        justify-content: center;
        flex-wrap: wrap;
        padding: 2rem;
    }

    .card {
        display: block;
        width: 300px;
        border-radius: 0.25rem;
        overflow: hidden;
        background-color: white;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        text-decoration: none;
        color: inherit;
        transition:
            transform 0.2s ease,
            box-shadow 0.2s ease;

        &:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        img {
            width: 100%;
            height: 200px;
            object-fit: contain;
        }

        @media (max-width: 768px) {
            width: calc(50% - 0.5rem);
            min-width: 140px;

            img {
                height: 150px;
            }
        }
    }

    .card-title {
        padding: 1rem;
        font-size: 1.1rem;
        font-weight: 400;

        @media (max-width: 768px) {
            padding: 0.75rem;
            font-size: 0.9rem;
        }
    }

    .card-label {
        margin-top: 0.5rem;
        font-size: 0.95rem;
        text-decoration: underline;
        color: #888;

        @media (max-width: 768px) {
            font-size: 0.85rem;
        }
    }
</style>
