<template>
	<div id="app">
		<Index></Index>
	</div>
</template>

<script>
import Index from './components/Index'

export default {
	name: 'App',
	components: {
		Index,
	},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Arvo:wght@700&family=Open+Sans&display=swap');

#app {
	padding: 1rem;

	font-family: 'Open Sans', Arial, sans-serif;
}

p {
	font-size: 14px;
	line-height: 130%;
}

h1 {
	font-family: 'Arvo', Georgia, serif;
}
</style>
