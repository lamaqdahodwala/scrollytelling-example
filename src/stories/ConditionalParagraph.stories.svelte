<script module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
  import ConditionalParagraph from '$lib/components/ConditionalParagraph.svelte';
	import {fade} from 'svelte/transition';

	const { Story } = defineMeta({
		title: "Components/ConditionalParagraph",
		component: ConditionalParagraph
	});


</script>

<Story
	name="Primary",
  args={{
    threshold: 0.5,
    progress: 0,
    text: "Test",
    elementHeight: 20
  }}

/>
