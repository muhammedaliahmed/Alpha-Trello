<template>
	<div>
		<LinkCard v-bind:link="link" v-on:del-link="deleteLink" />
	</div>
</template>

<script>
import LinkCard from "@/components/Link/LinkCard.vue";
import axios from "axios";

export default {
	name: "DisplayLink",
	components: { LinkCard },

	data() {
		return {
			link: [],
		};
	},

	methods: {
		deleteLink(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
				.then(() => (this.link = this.link.filter((loop) => loop.id !== id)))
				.catch((err) => console.log(err));
		},
	},

	created() {
		axios
			.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
			.then((res) => (this.link = res.data))
			.catch((err) => console.log(err));
	},
};
</script>

<style scoped></style>
