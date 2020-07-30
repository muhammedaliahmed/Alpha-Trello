<template>
	<div class="big-wrapper">
		<BoardNav></BoardNav>

		<div class="container">
			<div class="row">
				<div class="card-deck">
					<div class="card wrapper-card">
						<DisplayNews />
					</div>

					<div class="card wrapper-card"><DisplayLink /></div>

					<div class="card wrapper-card">
						<DisplayImage />
					</div>
				</div>
			</div>

			<div class="row">
				<div class="card-deck">
					<div class="card wrapper-card">
						<DisplayDocs />
					</div>

					<div class="card wrapper-card">
						<DisplayNews />
					</div>

					<div class="card wrapper-card">
						<DisplayLink />
					</div>
				</div>
			</div>
		</div>

		<!-- <div class="navbar navbar-expand-lg navbar-dark bg-dark">
			<span class="navbar-text">
				This is a board.
			</span>
		</div> -->
	</div>
</template>

<script>
import BoardNav from "@/components/BoardNav.vue";
import DisplayNews from "@/components/News/DisplayNews.vue";
import DisplayLink from "@/components/Link/DisplayLink.vue";
import DisplayImage from "@/components/Image/DisplayImage.vue";
import DisplayDocs from "@/components/Docs/DisplayDocs.vue";

//import CreatePoll from "@/components/Poll/CreatePoll.vue";
//import ViewPoll from "@/components/Poll/ViewPoll.vue";
//import axios from "axios";

export default {
	name: "Board",
	components: {
		BoardNav,
		DisplayNews,
		DisplayLink,
		DisplayImage,
		DisplayDocs,
		//CreatePoll,
	},

	data() {
		return {};
	},
};
</script>

<style scoper>
.big-wrapper {
	background-color: seagreen;
}

.cards-title {
	font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
}

.wrapper-card {
	margin-top: 2%;
	height: 500px;
	border-color: transparent;
	background-color: seagreen;
}

.scroll {
	height: 350px;
	overflow-y: auto;
}
</style>
