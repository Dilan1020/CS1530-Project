<template>
	<div class="home">
		<post 	v-for="post in posts"
				v-bind:key="post.id"
				v-bind:msg="post.postMessage"
				v-bind:votecount="post.score">
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
			// .get('http://3.22.49.236/getHomePosts?userLatitude=43&userLongitude=77.78&startIndex=0&retrieveLength=10')
			.get('http://localhost:8080/getHomePosts?userLatitude=43&userLongitude=77.78&startIndex=0&retrieveLength=100')
			.then(response => {
				this.sortByScore(response.data);
				this.posts = response.data;
				console.log(response.data);
			})
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
