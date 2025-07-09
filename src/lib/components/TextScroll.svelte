<script lang="ts">
	import ConditionalParagraph from './ConditionalParagraph.svelte';

	type ParagraphFormat = { text: string; threshold: number }[];
	let {
		height,
		progress,
		paragraphs
	}: { height: number; progress: number; paragraphs: ParagraphFormat } = $props();

	let elementHeights = [];
	for (let i = 0; i < paragraphs.length; i++) {
		if (i === paragraphs.length - 1) {
			elementHeights.push(1 - paragraphs[i].threshold);
      break
		}

		elementHeights.push(paragraphs[i + 1].threshold - paragraphs[i].threshold);
	}
</script>

<div style="height: {height * 100}vh;">
	<p>This is a demo that is exactly {height} screens</p>
	<p>Progress: {progress}</p>

	{#each paragraphs as pg, index}
		<ConditionalParagraph
			text={pg.text}
			{progress}
			elementHeight={elementHeights[index]}
			threshold={pg.threshold}
		></ConditionalParagraph>
	{/each}
</div>
