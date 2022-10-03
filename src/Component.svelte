<script>
  import { getContext } from "svelte"
  import katex from "katex";
	export let math;
	export let displayMode = false;
	
	const options = {
		displayMode: displayMode,
		throwOnError: false
	}
	
	$: katexString = katex.renderToString(math, options);

  const { styleable } = getContext("sdk")
  const component = getContext("component")
</script>

<div use:styleable={$component.styles}>
  {@html katexString}
</div>

<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css" integrity="sha384-AfEj0r4/OFrOo5t7NnNe46zW/tFgW6x/bCJG8FqQCEo3+Aro6EYUG4+cU+KJWu/X" crossorigin="anonymous">
</svelte:head>
