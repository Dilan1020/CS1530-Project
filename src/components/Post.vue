<template>
	<div class="post">
		<div class="message">
			<h4>{{ msg }}</h4>
		</div>

		<div class="vote">
				<font-awesome-icon v-on:click="voteUp" icon="angle-up" />
				<div class="votecount"> {{ votecount }} </div>
				<font-awesome-icon v-on:click="voteDown" icon="angle-down" />
		</div>
	</div>
</template>

<script>
export default {
	name: 'Post',
	props: {
		msg: String,
		votecount: Number,
		postID: Number
	},
	data: function() {
		return {
			// baseurl: 'http://3.22.49.236/postUpdatePostScore?postID='
			baseurl: 'http://localhost:8080/postUpdatePostScore?postID='
		}
	},
	methods: {
		voteUp: function(event) {
			let url = this.baseurl + this.postID + "&scoreOffset=1";
			this.axios
				.post(url)
				.then(response => {
					if (response.status == 200) {
						alert("Successfully incremented votecount");
					}
					console.log(response.data);
				})
				.catch(error => {
					console.log(error);
				});
			this.votecount++;
		},
		voteDown: function(event) {
			let url = this.baseurl + this.postID + "&scoreOffset=-1";
			this.axios
				.post(url)
				.then(response => {
					if (response.status == 200) {
						alert("Successfully decremented votecount");
					}
					console.log(response.data);
				})
				.catch(error => {
					console.log(error);
				});
			this.votecount--;
		}
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
