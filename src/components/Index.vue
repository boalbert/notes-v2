<template>
	<section>
		<CreateNote class="span-row" @update-notes="addNote"></CreateNote>

		<div class="grid-container">
			<Stats :note="notes"></Stats>
			<Note
				:note="note"
				v-for="(note, index) in notes"
				v-bind:key="note.id"
				@delete-note="removeNote(note.id, index)"
				@pin-note="pinNote(note.id, index)"
			>
			</Note>
		</div>
	</section>
</template>

<script>
import CreateNote from './CreateNote'
import Note from './Note'
import Stats from './Stats'
import axios from 'axios'

export default {
	name: 'Index',
	props: {},
	components: {
		CreateNote,
		Note,
		Stats,
	},
	data: function() {
		return {
			notes: [],
			stats: Object,
		}
	},
	methods: {
		addNote(note) {
			axios
				.post('http://localhost:8080/api/notes', note)
				.then((res) => {
					console.log(res)
				})
				.catch((error) => {
					console.log('Error posting data' + error)
				})
				.finally(() => {
					this.fetchData()
				})
		},

		fetchData() {
			fetch('http://localhost:8080/api/notes')
				.then((response) => {
					return response.json()
				})
				.then((data) => {
					this.notes = data
				})
		},
		removeNote(id, index) {
			// Send delete-request to API
			axios.delete('http://localhost:8080/api/notes/' + id)
			// Remove the note from array
			this.notes.splice(index, 1)
		},
		pinNote(id, index) {
			let today = new Date().toISOString().slice(0, 10)
			let updatedNote = this.notes[index]
			if (updatedNote.pinned) {
				updatedNote.pinned = false
			} else {
				updatedNote.pinned = true
			}
			updatedNote.dateEdited = today

			axios.put('http://localhost:8080/api/notes/' + id, updatedNote)
		},
	},
	mounted() {
		this.fetchData()
		// fetch('http://localhost:8080/api/notes')
		// 	.then((response) => {
		// 		return response.json()
		// 	})
		// 	.then((data) => {
		// 		this.notes = data
		// 	}),
		// 	fetch('http://localhost:8080/api/notes/stats')
		// 		.then((response) => {
		// 			return response.json()
		// 		})
		// 		.then((data) => {
		// 			this.stats = data
		// 		})
	},
}
</script>

<style>
.grid-container {
	display: flex;
	flex-wrap: wrap;
	flex-direction: row;
	gap: 1rem;
}

.span-row {
	justify-self: center;
}

section {
	display: grid;

	gap: 1rem;
}
</style>
