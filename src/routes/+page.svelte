<script lang="ts">
	import scrollama from 'scrollama';
	import { onMount } from 'svelte';
	import {
		Timeline,
		TimelineConnector,
		TimelineContent,
		TimelineDot,
		TimelineItem,
		TimelineOppositeContent,
		TimelineSeparator
	} from 'svelte-vertical-timeline';
	import { fade, fly } from 'svelte/transition';

	let stepIndex = $state();
	let directionOfScroll = $state();
	let progress: number = $state(0);

	import * as Plot from '@observablehq/plot';
	import TextScroll from '$lib/components/TextScroll.svelte';

	onMount(() => {
		let scroller = scrollama();

		scroller
			.setup({
				step: '.step',
				progress: true
			})
			.onStepEnter(({ index, direction }) => {
				stepIndex = index;
				directionOfScroll = direction;
			})
			.onStepProgress((response) => {
				progress = Number(response.progress);
			})
			.enable();
	});

	let events = ['2021', '2022', '2023', '2024'];

	let barChart: HTMLElement | undefined = $state();

	$effect(() => {
		barChart?.firstChild?.remove();
		barChart?.append(
			Plot.plot({
				marks: [Plot.barX([progress])],
				x: {
					domain: [0, 1],
					grid: true
				}
			})
		);
	});
</script>

<div class="grid h-screen items-center bg-green-100">
	<div>
		<h1 class="py-5 text-center text-8xl font-bold">An AI Future</h1>
		<p class="text-center text-xl">Lamaq Dahodwala and Joel Raj</p>
	</div>
</div>

<div class="fixed">{progress}</div>
<Timeline position="alternate">
	{#each events as i}
		<TimelineItem>
			<TimelineSeparator>
				<TimelineDot />
				<TimelineConnector />
			</TimelineSeparator>
			<TimelineContent>
				<div class=" h-96 grow">
					<p class="sticky top-1/2">{i}</p>
				</div>
			</TimelineContent>
			<TimelineOppositeContent slot="opposite-content">
				<div class="step">
					<div>
						<div bind:this={barChart}></div>
					</div>
					<TextScroll
						height={3}
						paragraphs={[
							{ text: 'hello', threshold: 0 },
							{ text: 'test', threshold: 0.3 },
							{ text: 'world', threshold: 0.6 }
						]}
						{progress}
					></TextScroll>
				</div>
			</TimelineOppositeContent>
		</TimelineItem>
	{/each}
</Timeline>
