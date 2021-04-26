<template>
	<div>
		<inputForm @update-notes="addNote"></inputForm>
		<ViewNotes
			:notes="notes"
			@delete-note="removeNote"
			@pin-note="pinNote"
		></ViewNotes>
	</div>
</template>

<script>
import inputForm from './PostNote'
import ViewNotes from './ViewNotes'
import axios from 'axios'

export default {
	name: 'Note',
	props: {},
	components: {
		inputForm,
		ViewNotes,
	},
	data: function() {
		return {
			notes: [],
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
			let updatedNote = this.notes[index]
			if (updatedNote.pinned) {
				updatedNote.pinned = false
			} else {
				updatedNote.pinned = true
			}

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
			})
	},
}
</script>

<style></style>
