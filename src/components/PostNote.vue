<template>
	<div class="form-box">
		<form id="note-form" @submit.prevent="submitNote(form)">
			<h1>MY NOTES 📚</h1>
			<label for="title">Title</label>
			<input type="text" name="title" v-model="form.title" />

			<label for="content">Content</label>
			<input type="text" name="content" v-model="form.content" />

			<button type="submit">💾</button>
		</form>
	</div>
</template>

<script>
// import axios from 'axios'

export default {
	name: 'inputForm',
	props: {
		name: String,
	},
	data() {
		return {
			form: {
				title: '',
				content: '',
				dateCreated: '',
				dateEdited: '',
			},
		}
	},
	methods: {
		submitNote(form) {
			this.$emit('update-notes', form)
			this.form.title = ''
			this.form.content = ''
		},
	},
	/*methods: {
		submitForm() {
			axios
				.post('http://localhost:8080/api/notes', this.form)
				.then((res) => {
					console.log(res)
					this.$emit('fetch-data')
				})
				.catch((error) => {
					console.log('Error posting data' + error)
				})
				.finally(() => {
					this.form.title = ''
					this.form.content = ''
					console.log('Finally executed after everything.')
				})
		},
	},*/
}
</script>

<style>
.form-box {
	border: 2px solid green;
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	width: 22rem;
	text-align: center;
	padding: 15px;
	background-color: white;
	border-radius: 5px;
	border: 1px solid lightgray;
}

.form-box > h1 {
	text-align: center;
}

button {
	font-size: 20px;
	border: none;
	background: none;
	cursor: pointer;
}

.form-box label {
	font-size: 14px;
	font-weight: bold;
	text-transform: uppercase;
}

input,
textarea {
	font-family: 'Open Sans', Arial, sans-serif;
	font-size: 15px;
	border: none;
	padding: 10px;
	width: 20rem;
	border-radius: 5px;
	background-color: #efefef;
}

textarea {
	resize: vertical;
	max-height: 250px;
}

input:focus,
textarea:focus {
	outline: none;
}
</style>
