<template>
	<div class="form-box">
		<form @submit.prevent="submitNote(form)">
			<input
				type="text"
				name="title"
				v-model="form.title"
				placeholder="Title"
			/>
			<textarea
				type="text"
				name="content"
				v-model="form.content"
				placeholder="Add a note..."
				maxlength="999"
				required
			/>

			<button type="submit">💾</button>
		</form>
	</div>
</template>

<script>
export default {
	name: 'CreateNote',
	props: {
		name: String,
	},
	data() {
		return {
			form: {
				title: '',
				content: '',
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
}
</script>

<style>
form {
	display: flex;
	flex-direction: column;
}
.form-box {
	width: 18rem;
	text-align: center;
	border-radius: 7px;
	/* max-height: 250px; */
	box-shadow: 0 0 8px 1px lightgray;
	border: 2px solid #e0e0e0;
	border-radius: 7px;
	padding: 5px;
}

button {
	font-size: 18px;
	border: none;
	background: none;
	cursor: pointer;
}

input {
	font-weight: bold;
}

input,
textarea {
	font-family: 'Open Sans', Arial, sans-serif;
	font-size: 15px;
	border: none;
	padding: 10px;
	width: 15rem;
	/* background-color: #efefef; */
}

textarea {
	resize: none;
}

input:focus,
textarea:focus {
	outline: none;
}
</style>
