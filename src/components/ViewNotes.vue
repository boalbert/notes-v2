<template>
	<div class="grid-container">
		<div class="note-item" v-for="(note, index) in notes" v-bind:key="note.id">
			<h2>
				{{ note.title }} (id: {{ note.id }}) <span v-if="note.pinned">〽</span>
			</h2>
			<p>{{ note.content }}</p>
			<p class="date">Created: {{ note.dateCreated }}</p>
			<button @click="deleteNote(note.id, index)">
				❌
			</button>
			<button @click="pinNote(note.id, index)">
				👍
			</button>
		</div>
	</div>
</template>

<script>
export default {
	name: 'ViewNotes',
	props: {
		notes: Array,
	},
	data: function() {
		return {}
	},
	methods: {
		deleteNote(id, index) {
			this.$emit('delete-note', id, index)
		},
		pinNote(id, index) {
			this.$emit('pin-note', id, index)
		},
	},
}
</script>

<style>
.grid-container {
	display: flex;
	flex-wrap: wrap;
	flex-direction: row;
	justify-content: flex-start;
	gap: 2rem;
	margin: 0 auto;
}

.note-item {
	background-color: white;
	border: 1px solid lightgray;
	border-radius: 5px;
	padding: 15px;
	max-width: 300px;
	transition: box-shadow 200ms;
	text-align: left;
}

.note-item:hover {
	box-shadow: 4px 4px 5px lightgray;
}

.date {
	font-size: 10px;
	color: darkgray;
	text-align: left;
}
</style>
