<template>
	<div class="home">
		<!-- TODO: update v-bind:key=ost.id or delete if not needed -->
		<!-- TODO: update v-bind:votecount when backend api is returning votecount -->
		<post 	v-for="post in posts"
				v-bind:key="post.id"
				v-bind:msg="post.postMessage"
				v-bind:votecount="post.score">
				<!-- v-bind:votecount="post.votecount"> -->
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
	mounted() {
		this.axios
			// .get('http://3.22.49.236/getHomePosts?userLatitude=43&userLongitude=77.78&startIndex=0&retrieveLength=10')
			.get('http://localhost:8080/getHomePosts?userLatitude=43&userLongitude=77.78&startIndex=0&retrieveLength=10')
			.then(response => {
				this.posts = response.data;
				console.log(response.data);
			})
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
