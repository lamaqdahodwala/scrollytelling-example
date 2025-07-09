<script module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
	import TextScroll from '$lib/components/TextScroll.svelte';
	import { onMount } from 'svelte';
	import scrollama from 'scrollama';

	const { Story } = defineMeta({
		title: "Components/TextScroll",
		component: TextScroll
	});

  let primaryArgs = {
		height: 1,
    progress: 0,
    paragraphs: ["Hello", "world", "test"],
    thresholds: [0, 0.5, 0.8]
	} 


</script>

<Story
	name="Primary",
  args={{
    height: 1,
    progress: 0, 
    paragraphs: [
      {text: "Demo", threshold: 0},
      {text: "Hello", threshold: 0.4},
      {text: "World", threshold: 0.9}
    ]
  }}
/>
