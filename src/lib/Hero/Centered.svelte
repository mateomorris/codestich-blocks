<script>
	import '../core.css';

	export let topper = 'Save Our Earth, One Person at a Time',
		title = `Let’s Go Green As It Makes Environment`,
		text = `We help companies develop powerful corporate social responsibility, grantmaking, and employee engagement strategies.`,
		buttons = [],
		background_image = null;
</script>

<section>
	<div class="container">
		<div class="content">
			<span class="topper">{topper}</span>
			<h1 class="title">{title}</h1>
			<p class="text">{text}</p>
			{#if buttons.length > 0}
				<div class="button-group">
					{#each buttons as { label, url }, i}
						{@const last = i === buttons.length - 1}
						<a href={url} class="button-solid" class:button1={!last} class:button2={last}>{label}</a
						>
					{/each}
				</div>
			{/if}
		</div>
	</div>

	{#if background_image}
		<picture class="background">
			<source media="(max-width: 600px)" srcset={background_image.mobile?.url} />
			<source media="(min-width: 601px)" srcset={background_image.desktop?.url} />
			<img
				loading="lazy"
				decoding="async"
				src={background_image.desktop?.url}
				alt="field"
				width="1920"
				height="1200"
				aria-hidden="true"
			/>
		</picture>
	{/if}
</section>

<style lang="postcss">
	/* Mobile - 360px */
	@media only screen and (min-width: 0rem) {
		section {
			/* Centers button */
			text-align: center;
			/* 200px - 300px - leaving extra space for the navigation */
			padding: clamp(12.5rem, 25.95vw, 18.75em) calc(16 / 16 * 1rem);
			/* prevents the topper line from causing an overflow */
			overflow: hidden;
			position: relative;
			z-index: 1;
			background-color: var(--background-color, blue);

			.background {
				width: 100%;
				height: 100%;
				display: block;
				position: absolute;
				top: 0;
				left: 0;
				z-index: -2;

				&:before {
					/* Overlay */
					content: '';
					width: 100%;
					height: 100%;
					background: #000;
					opacity: 0.48;
					position: absolute;
					display: block;
					top: 0;
					left: 0;
					z-index: 1;
					/* prevents the cursor from interacting with it */
					pointer-events: none;
				}

				img {
					position: absolute;
					top: 0;
					left: 0;
					height: 100%;
					width: 100%;
					object-fit: cover;
				}
			}

			.container {
				width: 100%;
				max-width: calc(1280 / 16 * 1rem);
				margin: auto;
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				align-items: center;
				gap: calc(48 / 16 * 1rem);
			}

			.content {
				width: 100%;
				max-width: calc(630 / 16 * 1rem);
			}

			.topper {
				/* 13px - 16px */
				font-size: clamp(0.8125rem, 1.5vw, 1rem);
				line-height: 1.2em;
				font-weight: 700;
				letter-spacing: 0.1em;
				text-align: center;
				text-transform: uppercase;
				margin-bottom: calc(16 / 16 * 1rem);
				color: var(--secondary);
				display: inline-block;
				position: relative;
			}

			.title {
				/* 39px - 61px */
				font-size: clamp(2.4375rem, 6.4vw, 3.8125rem);
				font-weight: 700;
				line-height: 1.2em;
				text-align: center;
				max-width: calc(829 / 16 * 1rem);
				/* 16px - 24px */
				margin: 0 auto clamp(1rem, 4vw, 1.5rem) 0;
				color: #fff;
				position: relative;
			}

			.text {
				/* 16px - 20px */
				font-size: clamp(1rem, 1.95vw, 1.25rem);
				line-height: 1.5em;
				text-align: center;
				width: 100%;
				/* 464px - 622px */
				max-width: clamp(29rem, 60vw, 38.785rem);
				margin: 0 auto 0;
				margin-bottom: calc(32 / 16 * 1rem);
				color: #fff;
			}

			.button-group {
				display: flex;
				justify-content: center;
				flex-wrap: wrap;
				gap: calc(8 / 16 * 1rem);
			}

			.button-solid {
				font-size: calc(16 / 16 * 1rem);
				/* 46px - 56px */
				line-height: clamp(2.875rem, 5.5vw, 3.5rem);
				text-decoration: none;
				font-weight: 700;
				text-align: center;
				margin: 0;
				color: #1a1a1a;
				min-width: calc(200 / 16 * 1rem);
				padding: 0 calc(24 / 16 * 1rem);
				background-color: var(--primary);
				border-radius: calc(8 / 16 * 1rem);
				display: inline-block;
				position: relative;
				z-index: 1;
				/* prevents padding from adding to the width */
				box-sizing: border-box;

				&:before {
					content: '';
					position: absolute;
					height: 100%;
					width: 0%;
					background: #000;
					opacity: 1;
					top: 0;
					left: 0;
					z-index: -1;
					border-radius: calc(4 / 16 * 1rem);
					transition: width 0.3s;
				}

				&:hover {
					&:before {
						width: 100%;
					}
				}
			}

			.button1 {
				background-color: var(--secondary);
			}
		}
	}
</style>
