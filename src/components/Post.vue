<template>
	<div class="post">
		<div class="message">
			<h4>{{ msg }}</h4>
			<div class="postDate">
				{{ this.formatDate(timestamp) }}
			</div>
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
		postID: Number,
		timestamp: String
	},
	data: function() {
		return {
			baseurl: 'http://localhost:8080/postUpdatePostScore?postID='
		}
	},
	methods: {
		formatDate(date) {
			let d = new Date(date);

            let usaTime = d.toLocaleString('en-US', { timeZone: 'UTC' });
			return usaTime;
			// return d.toUTCString();
			// let temp1 = date.replace("T", " ");
			// let temp2 = temp1.replace(".000Z", "");
			// return temp2;
		},
		voteUp: function(event) {
			let url = this.baseurl + this.postID + "&scoreOffset=1";
			this.axios
				.post(url)
				.then(response => {
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
