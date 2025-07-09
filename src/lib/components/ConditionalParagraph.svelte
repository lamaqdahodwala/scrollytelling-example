<script lang="ts">
	let {
		text,
		progress,
		threshold,
		elementHeight
	}: { text: string; progress: number; threshold: number; elementHeight: number } = $props();
	import { fade } from 'svelte/transition';
</script>

<div style="height: {elementHeight < 1 ? elementHeight * 100 : elementHeight}%">
	{#if progress > threshold}
		<div transition:fade={{ duration: 100 }} class="h-full">
      <p class="sticky top-1/4">{text}</p>
    </div>
	{/if}
</div>
