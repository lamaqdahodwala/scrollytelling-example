<script module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
	import TextScroll from '$lib/components/TextScroll.svelte';
	import { onMount } from 'svelte';
	import scrollama from 'scrollama';

	const { Story } = defineMeta({
		// title: "Components/TextScroll",
		component: TextScroll
	});


</script>

<Story
	name="Primary",
	args={{
		height: 3,
    progress: 0
	}},

/>
