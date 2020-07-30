<template>
	<div>
		<DocsCard v-bind:docs="docs" v-on:del-docs="deleteDocs" />
	</div>
</template>

<script>
import DocsCard from "@/components/Docs/DocsCard.vue";
import axios from "axios";

export default {
	name: "DisplayDocs",
	components: { DocsCard },

	data() {
		return {
			docs: [],
		};
	},

	methods: {
		deleteDocs(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/photos/${id}`)
				.then(() => (this.docs = this.docs.filter((loop) => loop.id !== id)))
				.catch((err) => console.log(err));
		},
	},

	created() {
		axios
			.get("https://jsonplaceholder.typicode.com/photos?_limit=5")
			.then((res) => (this.docs = res.data))
			.catch((err) => console.log(err));
	},
};
</script>

<style scoped></style>
