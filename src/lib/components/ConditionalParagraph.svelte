<script lang="ts">
	let { text, progress, threshold }: { text: string; progress: number, threshold: number} = $props();
  import { fade } from "svelte/transition";
</script>

{#if progress > threshold}
  <p transition:fade={{duration: 100}}>{text}</p>
{/if}
