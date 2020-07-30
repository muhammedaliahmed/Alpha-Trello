<template>
	<div>
		<!-- <input type="file" @change="onFileChanged" />
		<button @click="onUpload" class="btn btn-primary">+</button> -->

		<button
			type="button"
			class="btn btn-outline-success btn-lg btn-block"
			data-toggle="modal"
			data-target="#docsModal"
		>
			Upload documents
		</button>

		<div
			class="modal fade"
			id="docsModal"
			tabindex="-1"
			role="dialog"
			aria-labelledby="docsModal"
			aria-hidden="true"
		>
			<div class="modal-dialog modal-dialog-centered" role="document">
				<div class="modal-content">
					<div class="modal-header">
						<h5 class="modal-title">Upload documents</h5>
						<button
							type="button"
							class="close"
							data-dismiss="modal"
							aria-label="Close"
						>
							<span aria-hidden="true">&times;</span>
						</button>
					</div>

					<form @submit="adddocs">
						<div class="modal-body">
							<input type="file" @change="onFileChanged" />
						</div>

						<div class="modal-footer">
							<button @click="onUpload" class="btn btn-outline-success">
								Done
							</button>
						</div>
					</form>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import axios from "axios";

export default {
	name: "AddDocs",
	data() {
		return {
			title: "",
			selectedFile: null,
		};
	},
	methods: {
		addDocs(e) {
			e.preventDefault();
			const newDocs = {
				title: this.title,
			};
			this.$emit("add-docs", newDocs);

			this.title = "";
		},

		onFileChanged(event) {
			const file = event.target.files[0];
			return file;
		},

		onUpload() {
			axios.post(
				"https://jsonplaceholder.typicode.com/photos",
				this.selectedFile
			);
		},

		// onUpload() {
		// 	const formData = new FormData();
		// 	formData.append("myFile", this.selectedFile, this.selectedFile.name);
		// 	axios.post("my-domain.com/file-upload", formData);
		// },
	},
};
</script>

<style scoped></style>
