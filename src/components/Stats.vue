<template>
	<div class="stat-item">
		<h2>Stats</h2>
		<div>
			<p><b>Number of notes:</b> {{ stats.countNotes }}</p>
			<p><b>Pinned notes: </b> {{ stats.countPinned }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Stats',
	props: {
		stats: Object,
	},
	data: function() {
		return {}
	},
}
</script>

<style>
.stat-item {
	background-color: white;
	border: 1px solid lightgray;
	border-radius: 5px;
	padding: 15px;
	max-width: 300px;
	transition: box-shadow 200ms;
	text-align: left;
	width: 200px;
	height: 200px;
}
</style>
