<script>
	import { fade, fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center bg-gradient-to-b from-purple-800 to-slate-800 p-8"
>
	{#if mounted}
		<div
			class="max-w-2xl rounded-lg bg-white p-2 shadow-xl md:p-8"
			transition:fade={{ duration: 1000 }}
		>
			<!-- Header Section -->
			<h1
				class="wanted-text mb-2 text-center text-8xl font-bold uppercase tracking-wider text-red-600"
				in:fly={{ y: -50, duration: 1000, delay: 300 }}
			>
				Wanted
			</h1>

			<!-- Profile Section -->
			<div
				class="flex flex-col items-center space-y-4"
				in:fly={{ y: 50, duration: 1000, delay: 600 }}
			>
				<h2 class="glow text-4xl font-bold text-gray-800">Code Cowboy</h2>
				<p class="text-lg text-gray-600 md:text-xl">
					Web3 Engineer @ Magic Eden | Ex Google | Ex Meta
				</p>

				<!-- Image Container -->
				<div class="image-container relative overflow-hidden rounded-lg">
					<img class="h-64 w-64 object-cover" src="/cowboy.jpg" alt="Code Cowboy Profile" />
				</div>
			</div>

			<!-- Degen Badge -->
			<div class="my-6 flex justify-center" in:fly={{ y: 50, duration: 1000, delay: 900 }}>
				<a
					href="https://degenderby.io/"
					class="badge-hover transition-transform hover:scale-105"
					aria-label="Visit Degen Derby"
				>
					<img src="/degen.gif" alt="Degen Derby Badge" class="rounded-md" />
				</a>
			</div>

			<!-- Crime Description -->
			<h2
				class="crime-text my-6 text-center text-4xl font-bold uppercase text-red-600"
				in:fly={{ y: 50, duration: 1000, delay: 1200 }}
			>
				For Making a Bad Game
			</h2>

			<!-- CTA Button -->
			<div class="flex justify-center" in:fly={{ y: 50, duration: 1000, delay: 1500 }}>
				<a
					href="https://x.com/Code_Cowboy_"
					class="cta-button group relative rounded-lg bg-slate-800 px-6 py-3 font-bold text-white transition-all hover:bg-slate-700"
					target="_blank"
					rel="noopener noreferrer"
				>
					<span class="flex items-center space-x-2">
						<svg class="h-5 w-5" viewBox="0 0 24 24" fill="currentColor">
							<path
								d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
							/>
						</svg>
						<span>Follow Me on X!</span>
					</span>
				</a>
			</div>
		</div>
	{/if}
</div>

<style>
	/* Wanted Text Animation */
	.wanted-text {
		animation: textShadowPulse 2s infinite;
	}

	@keyframes textShadowPulse {
		0% {
			text-shadow: 0 0 4px rgba(220, 38, 38, 0.2);
		}
		50% {
			text-shadow: 0 0 16px rgba(220, 38, 38, 0.4);
		}
		100% {
			text-shadow: 0 0 4px rgba(220, 38, 38, 0.2);
		}
	}

	/* Glowing Text Effect */
	.glow {
		animation: glowPulse 3s infinite;
	}

	@keyframes glowPulse {
		0% {
			text-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
		}
		50% {
			text-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
		}
		100% {
			text-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
		}
	}

	/* Image Container Effects */
	.image-container {
		position: relative;
		transition: transform 0.3s ease;
	}

	.image-container:hover {
		transform: scale(1.05) rotate(2deg);
	}

	.image-container::after {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		border: 2px solid transparent;
		border-radius: 0.5rem;
		animation: borderFlash 4s infinite;
	}

	@keyframes borderFlash {
		0% {
			border-color: rgba(220, 38, 38, 0);
		}
		50% {
			border-color: rgba(220, 38, 38, 0.5);
		}
		100% {
			border-color: rgba(220, 38, 38, 0);
		}
	}

	/* Crime Text Animation */
	.crime-text {
		animation: shakeText 5s infinite;
	}

	@keyframes shakeText {
		0%,
		90%,
		94%,
		98%,
		100% {
			transform: translateX(0);
		}
		92% {
			transform: translateX(-3px) rotate(-1deg);
		}
		96% {
			transform: translateX(3px) rotate(1deg);
		}
	}

	/* CTA Button Animation */
	.cta-button {
		animation: pulse 2s infinite;
	}

	@keyframes pulse {
		0% {
			transform: scale(1);
		}
		50% {
			transform: scale(1.05);
		}
		100% {
			transform: scale(1);
		}
	}

	/* Badge Hover Effect */
	.badge-hover {
		transition: all 0.3s ease;
	}

	.badge-hover:hover {
		transform: translateY(-5px) rotate(3deg);
		filter: brightness(1.1);
	}
</style>
