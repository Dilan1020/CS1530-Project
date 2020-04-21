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
	methods: {
		cannotGetLocation() {
			alert("Geolocation is not supported by your browser");
		},
		getLocation(position) {
			this.latitude  = position.coords.latitude;
			this.longitude = position.coords.longitude;
			console.log("Getting posts based on my location: " + this.latitude + ", " + this.longitude);
		}
	},
	mounted() {
		if (!navigator.geolocation) {
			this.cannotGetLocation();
		} else {
			navigator.geolocation.getCurrentPosition(this.getLocation, this.cannotGetLocation);
		}

		this.axios
			.get(this.baseurl + 'userLatitude=' + this.latitude
						 + '&userLongitude=' + this.longitude
						 + '&startIndex=0&retrieveLength=100')
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
