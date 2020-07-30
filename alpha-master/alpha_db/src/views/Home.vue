<template>
	<div class="big-wrapper">
		<BoardNav />

		<div class="row home-card">
			<div class="col-sm-3" />
			<div class="col-sm-6">
				<DisplayHome />
			</div>
			<div class="col-sm-3" />
		</div>

		<Footer />
	</div>
</template>

<script>
import BoardNav from "@/components/Home/BoardNav.vue";
import DisplayHome from "@/components/Home/DisplayHome.vue";
import Footer from "@/components/Home/Footer.vue";

export default {
	name: "Home",
	components: { BoardNav, DisplayHome, Footer },

	data() {
		return {};
	},
};
</script>

<style scoped>
.home-card {
	margin: 2%;
}
</style>
