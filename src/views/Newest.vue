<template>
	<div class="home">
		<post 	v-for="post in posts"
				v-bind:key="post.id"
				v-bind:msg="post.msg"
				v-bind:votecount="post.votecount">
		</post>
		<!-- TODO: update post.id or delete if not needed -->
	</div>
</template>

<script>
import Post from '@/components/Post.vue'
export default {
	name: 'home',
		components: {
			Post
	},
	data() {
		return {
			//TODO: AJAX call or whatever to fetch real data and delete mock data
			posts: [
				{ msg: "hahaha", votecount: 10 },
				{ msg: "whatever", votecount: 23 },
				{ msg: "April 6th, monday, blablabla blablala \n whats up", votecount: -10 },
				{ msg: "April 6th, \n monday, \n blabl\nabla blablala \n whats up,\n something\aiyaya\ncfvgbhjnkmladgschjvnjknkajn\nvjkfnvkjanfjvnqjevnjlqnjlknlkj\nvnlkjanvkljanfjky", votecount: -100 }
			]
		}
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
