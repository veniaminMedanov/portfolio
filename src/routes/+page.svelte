<script lang="ts">
	import Main from '$lib/components/Main.svelte';

	let isHovering = $state(false);
	const radius = 100;
	let x = $state(0);
	let y = $state(0);

	function handlePointerMove(e: PointerEvent) {
		const rect = (e.currentTarget as HTMLElement).getBoundingClientRect();

		isHovering = true;

		x = e.clientX - rect.left;
		y = e.clientY - rect.top;
	}
</script>

<div
	class="relative min-h-screen w-screen bg-linear-to-br from-yellow-50 to-yellow-200"
	onpointerleave={() => (isHovering = false)}
	onpointermove={handlePointerMove}
	role="group"
>
	<!-- Hidden -->
	<div class="absolute z-10 h-full w-full text-green-500">Congrats if you found this!</div>

	<!-- Mask -->
	<div
		class="pointer-events-none absolute inset-0 z-20 h-full w-full bg-slate-950"
		style={isHovering
			? `
			mask-image: radial-gradient(circle ${radius}px at ${x}px ${y}px, transparent 0%, black 100%);
			-webkit-mask-image: radial-gradient(circle ${radius}px at ${x}px ${y}px, transparent 0%, black 100%);
		`
			: ''}
	></div>

	<main class="relative z-30 w-full">
		<Main />
	</main>
</div>
