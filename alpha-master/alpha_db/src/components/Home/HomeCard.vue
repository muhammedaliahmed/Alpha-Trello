<template>
	<div>
		<div class="card">
			<div class="card-header">
				Boards
			</div>
			<div class="card-body scroll">
				<ul class="list-group">
					<div v-bind:key="loop.id" v-for="loop in home">
						<li
							class="list-group-item d-flex justify-content-between align-items-center"
						>
							{{ loop.thumbnailUrl }}
							<router-link
								to="/Board"
								type="submit"
								name="submit"
								class="btn btn-outline-dark btn-md align-self-center"
								>Open Board</router-link
							>
						</li>
					</div>
				</ul>
			</div>
			<div class="card-footer">
				<AddHome v-on:add-home="addHome"></AddHome>
			</div>
		</div>
	</div>
</template>

<script>
import AddHome from "@/components/Home/AddHome.vue";
import axios from "axios";

export default {
	name: "HomeCard",
	components: {
		AddHome,
	},
	props: ["home"],

	methods: {
		addHome(newHome) {
			const { title } = newHome;

			axios
				.post("https://jsonplaceholder.typicode.com/photos", { title })

				.then((res) => (this.home = [...this.home, res.data]))
				.catch((err) => console.log(err));
		},
	},
};
</script>

<style scoped></style>
