<template>
	<div>
		<ImageCard v-bind:image="image" v-on:del-image="deleteImage" />
	</div>
</template>

<script>
import ImageCard from "@/components/Image/ImageCard.vue";
import axios from "axios";

export default {
	name: "DisplayImage",
	components: { ImageCard },

	data() {
		return {
			image: [],
		};
	},

	methods: {
		deleteImage(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/photos/${id}`)
				.then(() => (this.image = this.image.filter((loop) => loop.id !== id)))
				.catch((err) => console.log(err));
		},
	},

	created() {
		axios
			.get("https://jsonplaceholder.typicode.com/photos?_limit=3")
			.then((res) => (this.image = res.data))
			.catch((err) => console.log(err));
	},
};
</script>

<style scoped></style>
