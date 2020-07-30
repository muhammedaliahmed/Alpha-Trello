<template>
	<div>
		<NewsCard v-bind:content="content" v-on:del-content="deleteContent" />
	</div>
</template>

<script>
import NewsCard from "@/components/News/NewsCard.vue";
import axios from "axios";

export default {
	name: "DisplayNews",
	components: { NewsCard },

	data() {
		return {
			content: [],
		};
	},

	methods: {
		deleteContent(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
				.then(
					() => (this.content = this.content.filter((loop) => loop.id !== id))
				)
				.catch((err) => console.log(err));
		},
	},

	created() {
		axios
			.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
			.then((res) => (this.content = res.data))
			.catch((err) => console.log(err));
	},
};
</script>

<style scoped></style>
