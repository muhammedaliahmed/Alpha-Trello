<template>
	<div>
		<HomeCard v-bind:home="home" v-on:del-home="deleteHome" />
	</div>
</template>

<script>
import HomeCard from "@/components/Home/HomeCard.vue";
import axios from "axios";

export default {
	name: "DisplayHome",
	components: { HomeCard },

	data() {
		return {
			home: [],
		};
	},

	methods: {
		deleteHome(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/photos/${id}`)
				.then(() => (this.home = this.home.filter((loop) => loop.id !== id)))
				.catch((err) => console.log(err));
		},
	},

	created() {
		axios
			.get("https://jsonplaceholder.typicode.com/photos?_limit=5")
			.then((res) => (this.home = res.data))
			.catch((err) => console.log(err));
	},
};
</script>

<style scoped></style>
