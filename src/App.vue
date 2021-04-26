<template>
	<div id="app">
		<note></note>
	</div>
</template>

<script>
import Note from './components/Note'

export default {
	name: 'App',
	components: {
		Note,
	},
}
</script>
ViewNotes

<style>
@import url('https://fonts.googleapis.com/css2?family=Arvo:wght@700&family=Open+Sans&display=swap');

#app {
	padding: 15px;
	display: flex;
	justify-content: flex-start;
	gap: 2rem;
	flex-direction: row;
	flex-wrap: wrap;
	background-color: #efefef;
	font-family: 'Open Sans', Arial, sans-serif;
	text-align: center;
}

p {
	font-size: 14px;
	line-height: 130%;
}

h1 {
	font-family: 'Arvo', Georgia, serif;
}
</style>
