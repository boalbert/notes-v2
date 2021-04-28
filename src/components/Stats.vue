// Component not in use atm

<template>
	<div class="stat-item" v-if="note.length > 0">
		<h1>Stats</h1>
		<div>
			<p><b>Pinned notes:</b> {{ countPinned }}</p>
			<p><b>Contact:</b> {{ countTheWordContact }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Stats',
	props: {
		note: Array,
	},
	data: function() {
		return {}
	},
	computed: {
		countPinned: function() {
			let countPinned = 0

			for (let i = 0; i < this.note.length; i++) {
				if (this.note[i].pinned) {
					countPinned++
				}
			}
			return countPinned
		},
		countTheWordContact: function() {
			let countContact = 0

			for (let i = 0; i < this.note.length; i++) {
				let desc = this.note[i].content.toLowerCase()

				if (desc.includes('contact')) {
					countContact++
				}
			}
			return countContact
		},
	},
}
</script>

<style>
.stat-item {
	padding: 15px;
	border: 1px solid #e0e0e0;
	border-radius: 7px;
	max-width: 300px;
	text-align: left;
	min-width: 150px;
	height: 150px;
}
</style>
