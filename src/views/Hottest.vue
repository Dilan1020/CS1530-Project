<template>
	<div class="home">
		<post 	v-for="post in posts"
				v-bind:postID="post.postID"
				v-bind:msg="post.postMessage"
				v-bind:votecount="post.score"
				v-bind:timestamp="post.postCreated">
		</post>
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
			posts: null
		}
	},
	methods: {
		sortByScore: function(posts) {
			return posts.sort((a, b) => a.score < b.score ? 1: -1);
		}
	},
	mounted() {
		this.axios
			.get('http://localhost:8080/getHomePosts?userLatitude=43&userLongitude=77.78&startIndex=0&retrieveLength=100')
			.then(response => {
				this.sortByScore(response.data);
				this.posts = response.data;
				console.log(response.data);
			});
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
