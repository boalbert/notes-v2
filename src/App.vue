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
	border: 2px solid red;
	display: flex;
	justify-content: flex-start;
	padding: 15px;
	gap: 2rem;
	flex-direction: row;
	flex-wrap: wrap;
	background-color: #efefef;
	font-family: 'Open Sans', Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

p {
	font-size: 14px;
	line-height: 130%;
}

h1 {
	font-family: 'Arvo', Georgia, serif;
	font-size: 30px;
}

h2 {
	font-size: 25px;
}

h3 {
	font-size: 20px;
}
</style>
