<template>
	<div>
		<button
			type="button"
			class="btn btn-outline-success btn-lg btn-block"
			data-toggle="modal"
			data-target="#newsModal"
		>
			Share news
		</button>

		<div
			class="modal fade"
			id="newsModal"
			tabindex="-1"
			role="dialog"
			aria-labelledby="newsModal"
			aria-hidden="true"
		>
			<div class="modal-dialog modal-dialog-centered" role="document">
				<div class="modal-content">
					<div class="modal-header">
						<h5 class="modal-title">Share news</h5>
						<button
							type="button"
							class="close"
							data-dismiss="modal"
							aria-label="Close"
						>
							<span aria-hidden="true">&times;</span>
						</button>
					</div>

					<form @submit="addContent">
						<div class="modal-body">
							<input
								type="text"
								required
								v-model="title"
								name="title"
								class="form-control"
								placeholder="Say something"
								aria-label="Say something"
								aria-describedby="basic-addon2"
							/>
						</div>
						<div class="modal-footer">
							<input
								type="submit"
								value="Done"
								class="btn btn-outline-success"
							/>
						</div>
					</form>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "AddContent",
	data() {
		return {
			title: "",
		};
	},
	methods: {
		addContent(e) {
			e.preventDefault();
			const newContent = {
				title: this.title,
			};
			this.$emit("add-content", newContent);

			this.title = "";
		},
	},
};
</script>

<style scoped></style>
