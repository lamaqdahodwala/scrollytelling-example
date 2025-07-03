<script lang="ts">
	import scrollama from 'scrollama';
	import { onMount } from 'svelte';

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
</script>

<div class="fixed right-[5%] h-48 border border-1 border-black bg-red-200 p-3">
	<p>Current step: {stepIndex}</p>
	<p>Direction that step was triggered: {directionOfScroll}</p>
</div>
<div class="fixed right-[25%] h-48 border border-1 border-black bg-blue-100 p-3">
	<p>Your progress through the step</p>
	<div id="progress-container" class="h-8 w-full bg-gray-300">
		<div
			id="progress-bar"
			style="width: {progress * 100}%"
			class="flex h-8 flex-row justify-center bg-green-800"
		></div>
	</div>
	{progress}
</div>

<div class="">
	<div class="step h-screen font-bold">Hello, I'm step 0</div>
<div>
	<div class="step h-screen font-bold">Hello, I'm step 1</div>
  <div class="sticky top-1/2">This is a sticky div</div>
	<div class="step h-screen font-bold">Hello, I'm step 2</div></div>
	<div class="step h-screen font-bold">Hello, I'm step 3</div>
</div>
