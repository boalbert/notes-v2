<template>
	<section>
		<inputForm @update-notes="addNote"></inputForm>
		<Stats :stats="stats"></Stats>
		<ViewNotes
			:notes="notes"
			@delete-note="removeNote"
			@pin-note="pinNote"
		></ViewNotes>
	</section>
</template>

<script>
import inputForm from './PostNote'
import ViewNotes from './ViewNotes'
import Stats from './Stats'
import axios from 'axios'

export default {
	name: 'Note',
	props: {},
	components: {
		inputForm,
		ViewNotes,
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
		fetch('http://localhost:8080/api/notes')
			.then((response) => {
				return response.json()
			})
			.then((data) => {
				this.notes = data
			}),
			fetch('http://localhost:8080/api/notes/stats')
				.then((response) => {
					return response.json()
				})
				.then((data) => {
					this.stats = data
				})
	},
}
</script>

<style>
section {
	display: flex;
	gap: 1rem;
}
</style>
