<script>
    import Icon from "@iconify/svelte";
    import { slide } from "svelte/transition";

    const featureIcons = {
        Bluetooth: "material-symbols:bluetooth-rounded",
        "Long-Lasting Battery": "gg:battery",
        "Multi-device Pairing": "tabler:category",
    };

    const tags = $state(["Featured"]);
    const price = $state(60);
    const product = $state({
        name: "Razer Basilisk x Hyperspeed Wireless Gaming Mouse",
        description: [
            "🖱️ Wireless Dual Mode – HyperSpeed (2.4 GHz) or Bluetooth",
            "⚡ Ultra-low latency in HyperSpeed mode (almost like wired)",
            "🎯 16,000 DPI sensor – Accurate & responsive tracking",
            "⚙️ 6 programmable buttons – Customisable with Razer Synapse",
            "⏱️ 50M click durability – Mechanical switches built to last",
            "🔋 Battery life – Up to 285 hrs (HyperSpeed) / 450 hrs (Bluetooth)",
            "🖐️ Ergonomic design – Right-handed with thumb rest, 83g lightweight. Great for long gaming sessions.",
            "🛠️ Durable build – Reliable switches for heavy gaming use",
        ],
        image: "/files/mouse6.jpg",
        originalPrice: 60,
        features: [
            "Bluetooth",
            "Long-Lasting Battery",
            "Multi-device Pairing",
        ],
        includes: [
            "1x Razer Basilisk x Hyperspeed Wireless Gaming Mouse",
            "1x Dongle Receiver",
            "1x AA Battery (Pre-installed)",
        ],
        brand: "GamaKay",
        condition: "New",
    });

    let productInfoSections = $state([
        {
            title: "Specs & Details",
            intro: "Take your gameplay to the next level with the Razer Basilisk X Hyperspeed – a high-performance, wireless gaming mouse engineered for speed, precision, and long-lasting power, all in a lightweight design.",
            listItems: product.description,
            open: false,
        },
        {
            title: "What's in the box?",
            intro: "Package includes:",
            listItems: product.includes,
            open: false,
        },
    ]);

    let faqs = $state([
        {
            question: "How can I pay for this listing?",
            answer: " Click on the above 'Buy Now' button to proceed to Carousell.<br><br>Once you're on Carousell, tap on the 'Buy' button to pay securely via Carousell. Pay directly with your credit/debit card, DBS PayLah! or PayNow—no additional set-ups or wallet top-ups needed.",
            open: false,
        },
        {
            question: "What is Buyer Protection?",
            answer: "Your purchase is covered by Buyer Protection when you pay via the 'Buy' button. This means you'll get a full refund if the item doesn't arrive, is damaged during delivery, or is not what you saw in the listing.<br><br><a href='https://support.carousell.com/hc/en-us/articles/360038048693--Singapore-What-does-Buyer-Protection-cover' target='_blank' rel='noopener'>Learn More</a>",
            open: false,
        },
        {
            question: "How do I request for a return or refund?",
            answer: "Just tap on 'Return/refund' on your order details page if something goes wrong with your order. Carousell will reach out to you via email within 24h to resolve the issue.<br><br><a href='https://support.carousell.com/hc/en-us/articles/360001548627--Singapore-How-do-I-raise-a-return-refund-request' target='_blank' rel='noopener'>Learn More</a>",
            open: false,
        },
        {
            question: "What type of connection does it support?",
            answer: "It supports 2.4GHz Dongle Receiver and Bluetooth.",
            open: false,
        },
        {
            question: "How long does shipping take?",
            answer: "3-5 days after seller ships your order, with tracking.",
            open: false,
        },
    ]);

    const mediaItems = $state([
        { type: "image", src: "/files/mouse6.jpg", alt: "View 1" },
        { type: "image", src: "/files/mouse7.jpg", alt: "View 2" },
        { type: "image", src: "/files/mouse8.jpg", alt: "View 3" },
    ]);

    let currentSlide = $state(0);
    let isDesktop = $state(true);

    function nextSlide() {
        currentSlide = (currentSlide + 1) % mediaItems.length;
    }

    function prevSlide() {
        currentSlide =
            (currentSlide - 1 + mediaItems.length) % mediaItems.length;
    }

    function goToSlide(index) {
        currentSlide = index;
    }

    function toggleSection(sections, index) {
        return sections.map((section, i) => ({
            ...section,
            open: i === index ? !section.open : section.open,
        }));
    }

    function toggleProductInfo(index) {
        productInfoSections = toggleSection(productInfoSections, index);
    }

    function toggleFAQ(index) {
        faqs = toggleSection(faqs, index);
    }

    function checkScreenSize() {
        isDesktop = window.innerWidth >= 768;
    }

    $effect(() => {
        if (typeof window !== "undefined") {
            checkScreenSize();
            window.addEventListener("resize", checkScreenSize);
            return () => window.removeEventListener("resize", checkScreenSize);
        }
    });
</script>

<main class="main">
    <section class="section">
        <div class="container">
            <section class="left-content">
                {#if isDesktop}
                    <img
                        src={mediaItems[0].src}
                        alt={mediaItems[0].alt}
                        class="product-image"
                    />

                    <div class="image-stack">
                        {#each mediaItems as item, index}
                            {#if index > 0 && item.type === "image"}
                                <img
                                    src={item.src}
                                    alt={item.alt}
                                    class="product-image"
                                />
                            {:else if item.type === "video" && index > 0}
                                <video
                                    src={item.src}
                                    controls
                                    class="product-video"
                                ></video>
                            {/if}
                        {/each}
                    </div>
                {:else}
                    <div class="carousel-container">
                        <div class="carousel-slide">
                            {#if mediaItems[currentSlide].type === "image"}
                                <img
                                    src={mediaItems[currentSlide].src}
                                    alt={mediaItems[currentSlide].alt}
                                    class="carousel-image"
                                />
                            {:else}
                                <video
                                    src={mediaItems[currentSlide].src}
                                    class="carousel-video"
                                    controls
                                ></video>
                            {/if}
                        </div>

                        <button
                            class="carousel-button prev-button"
                            onclick={prevSlide}
                        >
                            <Icon
                                icon="mingcute:left-line"
                                width="24"
                                height="24"
                            />
                        </button>

                        <button
                            class="carousel-button next-button"
                            onclick={nextSlide}
                        >
                            <Icon
                                icon="mingcute:right-line"
                                width="24"
                                height="24"
                            />
                        </button>

                        <div class="carousel-indicators">
                            {#each mediaItems as _, index}
                                <button
                                    class="indicator-dot {currentSlide === index
                                        ? 'active'
                                        : ''}"
                                    onclick={() => goToSlide(index)}
                                ></button>
                            {/each}
                        </div>
                    </div>
                {/if}
            </section>

            <section class="right-content">
                <div class="product-tags">
                    {#each tags as tag}
                        <span class="tag">{tag}</span>
                    {/each}
                </div>
                <h1 class="product-title">{product.name}</h1>
                <div class="product-pricing">
                    <span class="regular-price"
                        >S${product.originalPrice.toFixed(2)}</span
                    >
                </div>
                <div class="product-features">
                    <h3 class="features-title">Features</h3>
                    <div class="features-list">
                        {#each product.features as feature}
                            <div class="feature-item">
                                <Icon
                                    icon={featureIcons[feature]}
                                    width="24"
                                    height="24"
                                    class="feature-icon"
                                />
                                <span class="feature-text">{feature}</span>
                            </div>
                        {/each}
                    </div>
                </div>

                <section class="collapsible-section product-info-section">
                    <ul class="collapsible-list">
                        {#each productInfoSections as section, i}
                            <li class="collapsible-item">
                                <button
                                    class="collapsible-header"
                                    onclick={() => toggleProductInfo(i)}
                                >
                                    {section.title}
                                    <span class="toggle-icon"
                                        >{section.open ? "−" : "+"}</span
                                    >
                                </button>
                                {#if section.open}
                                    <div
                                        class="collapsible-content"
                                        transition:slide
                                    >
                                        {#if section.intro}
                                            <p>{@html section.intro}</p>
                                        {/if}
                                        <ul class="info-list">
                                            {#each section.listItems as item}
                                                <li>{item}</li>
                                            {/each}
                                        </ul>
                                    </div>
                                {/if}
                            </li>
                        {/each}
                    </ul>
                </section>

                <a
                    href="https://www.carousell.sg/p/razer-basilisk-x-hyperspeed-wireless-gaming-mouse-1394689270/?t-id=l81nBLJZiy_1759239757222&t-referrer_browse_type=seller&t-referrer_page_type=profile&t-referrer_request_id=FZyE_MpoSwisgJ3Y&t-tap_index=1"
                    target="_blank"
                >
                    <button class="action-button">Buy Now</button>
                </a>

                <section class="description">
                    <section class="collapsible-section faq-section">
                        <h2 class="section-title">FAQ</h2>
                        <ul class="collapsible-list">
                            {#each faqs as faq, i}
                                <li class="collapsible-item">
                                    <button
                                        class="collapsible-header"
                                        onclick={() => toggleFAQ(i)}
                                    >
                                        {faq.question}
                                        <span class="toggle-icon"
                                            >{faq.open ? "−" : "+"}</span
                                        >
                                    </button>
                                    {#if faq.open}
                                        <div
                                            class="collapsible-content"
                                            transition:slide
                                        >
                                            {@html faq.answer}
                                        </div>
                                    {/if}
                                </li>
                            {/each}
                        </ul>
                    </section>
                </section>
            </section>
        </div>
    </section>
</main>

<style lang="scss">
    .main {
        min-height: 100vh;
        background-color: white;
        color: #1f2937;
        display: flex;
        flex-direction: column;
        align-items: center;

        .section {
            padding: 7rem 0;
            background-color: #f9fafb;
            width: 100%;

            .container {
                display: flex;
                flex-direction: column;
                padding: 0 0.8rem;
                gap: 1.5rem;
                align-items: flex-start;
                justify-content: center;
                margin: 0 auto;

                @media (min-width: 768px) {
                    flex-direction: row;
                }

                .left-content {
                    display: flex;
                    flex-direction: column;
                    width: 100%;

                    @media (min-width: 768px) {
                        width: 50%;
                    }

                    .product-image,
                    .product-video {
                        aspect-ratio: 1 / 1;
                        margin-bottom: 1rem;
                        border-radius: 0.25rem;
                        width: 100%;
                        max-width: 70rem;
                        object-fit: cover;
                        height: auto;
                        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
                    }

                    .image-stack {
                        display: flex;
                        flex-direction: column;
                        gap: 1rem;
                    }

                    .carousel-container {
                        position: relative;
                        width: 100%;
                        overflow: hidden;
                        border-radius: 0.25rem;

                        .carousel-slide {
                            width: 100%;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                        }

                        .carousel-image,
                        .carousel-video {
                            max-width: 100%;
                            max-height: 100%;
                            object-fit: cover;
                            aspect-ratio: 4 / 3;
                            border-radius: 0.25rem;
                        }

                        .carousel-button {
                            position: absolute;
                            top: 50%;
                            transform: translateY(-50%);
                            background-color: rgba(255, 255, 255, 0.3);
                            color: rgba(255, 255, 255, 0.5);
                            border: none;
                            border-radius: 50%;
                            width: 2rem;
                            height: 2rem;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            cursor: pointer;
                            z-index: 10;
                            transition: background-color 0.3s;

                            &.prev-button {
                                left: 0.5rem;
                            }

                            &.next-button {
                                right: 0.5rem;
                            }
                        }

                        .carousel-indicators {
                            position: absolute;
                            bottom: 0.5rem;
                            left: 0;
                            right: 0;
                            display: flex;
                            justify-content: center;
                            gap: 0.5rem;
                            z-index: 10;

                            .indicator-dot {
                                width: 0.5rem;
                                height: 0.5rem;
                                border-radius: 50%;
                                background-color: rgba(255, 255, 255, 0.5);
                                border: none;
                                cursor: pointer;
                                transition: background-color 0.3s;

                                &.active {
                                    background-color: white;
                                }
                            }
                        }
                    }
                }

                .right-content {
                    width: 100%;

                    @media (min-width: 768px) {
                        width: 50%;
                    }

                    .product-tags {
                        margin-bottom: 0.8rem;
                        display: flex;
                        flex-wrap: wrap;
                        gap: 0.5rem;

                        .tag {
                            background-color: black;
                            color: white;
                            font-size: 0.75rem;
                            padding: 0.3rem 0.75rem;
                            border-radius: 25px;
                            font-weight: 500;

                            @media (min-width: 768px) {
                                font-size: 1rem;
                                padding: 0.4rem 1rem;
                            }
                        }
                    }

                    .product-title {
                        font-size: 1.5rem;
                        font-weight: 500;
                        margin-bottom: 1rem;

                        @media (min-width: 768px) {
                            font-size: 1.75rem;
                        }
                    }

                    .product-pricing {
                        display: flex;
                        align-items: center;
                        gap: 0.5rem;
                        margin: 1rem 0;

                        .regular-price {
                            font-weight: bold;
                            color: #333;
                        }
                    }

                    .product-features {
                        margin-top: 1rem;

                        .features-title {
                            font-weight: 200;
                            margin-bottom: 0.5rem;

                            @media (min-width: 768px) {
                                font-size: 1.25rem;
                            }
                        }

                        .features-list {
                            display: flex;
                            flex-wrap: wrap;

                            .feature-item {
                                display: flex;
                                flex-direction: column;
                                align-items: center;
                                text-align: center;
                                padding: 0.4rem 0.5rem;
                                border-radius: 0.5rem;
                                font-size: 0.85rem;
                                font-weight: 500;
                                white-space: nowrap;

                                @media (min-width: 768px) {
                                    font-size: 1rem;
                                }

                                .feature-icon,
                                .feature-text {
                                    font-weight: 600;
                                    color: rgba(0, 0, 0, 0.7);
                                }

                                .feature-text {
                                    margin-top: 0.5rem;
                                }
                            }
                        }
                    }

                    .action-button {
                        width: 100%;
                        background-color: black;
                        color: white;
                        padding: 0.75rem 1.5rem;
                        border-radius: 0.25rem;
                        transition: background-color 0.3s ease;
                        border: none;
                        cursor: pointer;
                    }

                    .collapsible-section {
                        width: 100%;
                        margin-bottom: 1rem;
                        overflow: hidden;

                        .section-title {
                            font-size: 1.25rem;
                            margin-left: 1rem;
                        }

                        .collapsible-list {
                            list-style: none;
                            padding: 0;
                            margin: 0;

                            .collapsible-item {
                                border-bottom: 1px solid #e5e7eb;

                                .collapsible-header {
                                    background: none;
                                    border: none;
                                    width: 100%;
                                    text-align: left;
                                    display: flex;
                                    justify-content: space-between;
                                    align-items: center;
                                    padding: 1rem;
                                    cursor: pointer;
                                    font-weight: 500;
                                    transition: background-color 0.2s;

                                    &:hover {
                                        background-color: #f9fafb;
                                    }

                                    .toggle-icon {
                                        font-size: 1.25rem;
                                        color: #6b7280;
                                        font-weight: 300;
                                    }
                                }

                                .collapsible-content {
                                    padding: 1rem;
                                    background-color: #f9fafb;
                                    color: #6b7280;

                                    p {
                                        margin-top: 0;
                                        margin-bottom: 0.75rem;

                                        &:last-child {
                                            margin-bottom: 0;
                                        }
                                    }

                                    a {
                                        color: #1f2937;
                                        text-decoration: underline;
                                    }

                                    .info-list {
                                        list-style: none;
                                        padding: 0;
                                        margin: 0;

                                        li {
                                            margin-bottom: 0.5rem;
                                            position: relative;
                                            padding-left: 1.5rem;

                                            &:before {
                                                content: "•";
                                                position: absolute;
                                                left: 0.5rem;
                                                font-size: 1.25rem;
                                                color: #d1d5db;
                                            }

                                            &:last-child {
                                                margin-bottom: 0;
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }

                    .product-info-section {
                        margin-top: 1.5rem;
                    }

                    .faq-section {
                        margin-top: 2rem;
                    }
                }
            }
        }
    }
</style>
