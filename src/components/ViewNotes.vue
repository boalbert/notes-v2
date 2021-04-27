<template>
	<div class="grid-container">
		<!-- Pinned items -->

		<div v-for="(note, index) in notes" v-bind:key="note.id" class="note-item">
			<p class="note-header">
				{{ note.title }}<span v-if="note.pinned">〽</span>
			</p>
			<p>{{ note.content }}</p>
			<p class="date">Created: {{ note.dateCreated }}</p>
			<p class="date" v-show="note.dateEdited">Edited: {{ note.dateEdited }}</p>
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

.note-header {
	font-size: 16px;
	font-weight: bold;
	padding: 0;
	margin: 0;
}

.note-item:hover {
	box-shadow: 4px 4px 5px lightgray;
}

.span-row {
	flex-basis: 100%;
	border-bottom: 2px solid black;
}

.date {
	font-size: 10px;
	color: darkgray;
	text-align: left;
}
</style>
