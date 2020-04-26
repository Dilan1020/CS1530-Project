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
			baseurl:'http://localhost:8080/getHomePosts?',
			posts: null,
			latitude: null,
			longitude: null
		}
	},
	mounted() {
		var getPosition = function (options) {
			return new Promise(function (resolve, reject) {
				navigator.geolocation.getCurrentPosition(resolve, reject, options);
				});
		}

		getPosition()
			.then((position) => {
				this.latitude  = position.coords.latitude;
				this.longitude = position.coords.longitude;
				console.log("Getting posts nearest to: " + this.latitude + ", " + this.longitude);

				let url = this.baseurl + 'userLatitude=' + this.latitude
							 + '&userLongitude=' + this.longitude
							 + '&startIndex=0&retrieveLength=100';
				console.log("url: " + url);

				this.axios
					.get(this.baseurl + 'userLatitude=' + this.latitude
								 + '&userLongitude=' + this.longitude
								 + '&startIndex=0&retrieveLength=100')
					.then(response => {
						this.posts = response.data;
						console.log(response.data);
					})
		})
		.catch((err) => {
			console.error(err.message);
		});
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
