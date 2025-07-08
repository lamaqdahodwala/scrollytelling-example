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
</script>

<div class="grid h-screen items-center bg-green-100">
	<div>
		<h1 class="text-center text-8xl font-bold py-5">An AI Future</h1>
		<p class="text-center text-xl">Lamaq Dahodwala and Joel Raj</p>
	</div>
</div>

<div class="fixed"></div>
<Timeline position="alternate">
	{#each events as i}
		<TimelineItem>
			<TimelineSeparator>
				<TimelineDot />
				<TimelineConnector />
			</TimelineSeparator>
			<TimelineContent>
				<div class="step h-screen grow">
					<p class="sticky top-1/2">{i}</p>
				</div>
			</TimelineContent>
			<TimelineOppositeContent slot="opposite-content">
				<div>
					<p class="h-64">{progress}</p>
				</div>
			</TimelineOppositeContent>
		</TimelineItem>
	{/each}
</Timeline>
