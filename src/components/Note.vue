<template>
	<article class="note-item">
		<!-- Header -->
		<div class="note-header">
			<h3><span v-if="note.pinned">+</span>{{ note.title }}</h3>

			<div class="note-buttons">
				<p @click="pinNote(note.id, index)">
					📌
				</p>
				<p @click="deleteNote(note.id, index)">
					❌
				</p>
			</div>
		</div>

		<!-- Content -->
		<div class="note-content">
			{{ note.content }}
		</div>

		<!-- Date -->
		<div class="note-date">
			<p v-if="!note.dateEdited">Created: {{ note.dateCreated }}</p>
			<p v-show="note.dateEdited">Edited: {{ note.dateEdited }}</p>
		</div>
	</article>
</template>

<script>
export default {
	name: 'Note',
	props: {
		note: Object,
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
p {
	word-break: break-all;
}
.note-item {
	padding: 15px;
	display: grid;
	border: 1px solid #e0e0e0;
	border-radius: 7px;
	transition: box-shadow 100ms;
	text-align: left;
	width: 200px;
}

.note-item:hover {
	box-shadow: 0 0 8px 1px lightgray;
}

.note-header {
	display: flex;
	justify-content: space-between;
	flex-direction: row;
	font-size: 16px;
	font-weight: bold;
	padding: 0;
}

.note-content {
	font-size: 14px;
}

.note-date {
	display: flex;
	color: darkgray;
}

.note-date p {
	font-size: 11px;
}

.note-buttons {
	opacity: 0;
	display: flex;
	color: transparent;
	text-shadow: 0 0 0 darkgrey;
	font-size: 13px;
	text-align: right;
	cursor: pointer;
}

.note-buttons button {
	color: transparent;
	text-shadow: 0 0 0 darkgrey;
	font-size: 13px;
}

.note-item:hover .note-buttons {
	opacity: 1;
}
</style>
