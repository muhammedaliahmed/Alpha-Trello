<template>
	<div class="card">
		<div class="card-header cards-title">
			Images
		</div>
		<div class="card-body scroll">
			<ul class="list-group">
				<div v-bind:key="loop.id" v-for="loop in image">
					<li
						class="list-group-item d-flex justify-content-between align-items-center"
					>
						<img :src="loop.thumbnailUrl" />
						<button
							@click="$emit('del-image', loop.id)"
							type="button"
							class="close"
							aria-label="Close"
						>
							<span aria-hidden="true">&times;</span>
						</button>
					</li>
				</div>
			</ul>
		</div>
		<div class="card-footer image-footer text-muted">
			<AddImage v-on:add-image="addImage"></AddImage>
		</div>
	</div>
</template>

<script>
import AddImage from "@/components/Image/AddImage.vue";
import axios from "axios";

export default {
	name: "ImageCard",
	components: {
		AddImage,
	},
	props: ["image"],

	methods: {
		addImage(newImage) {
			const { thumbnailUrl } = newImage;

			axios
				.post("https://jsonplaceholder.typicode.com/photos", { thumbnailUrl })

				.then((res) => (this.image = [...this.image, res.data]))
				.catch((err) => console.log(err));
		},
	},
};
</script>

<style scoped></style>
