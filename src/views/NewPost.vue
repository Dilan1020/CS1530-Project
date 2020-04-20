<template>
	<div class="newpostcontainer">
		<textarea v-model="postmessage" class="posttext"></textarea>
		<button v-on:click="clickHandler" class="postbutton">POST</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			postmessage: '',
			baseurl: 'http://localhost:8080/postNewPost?'
		}
	},
	methods: {
		clickHandler: function(event) {
			console.log(this.postmessage);

			//TODO: use actual geolocation
			let url = this.baseurl + 'userLatitude=43.094337&userLongitude=-77.772974' + '&postText=' + this.postmessage;
			this.axios
				.post(url)
				.then(response => {
					console.log(response.data);
					if (response.status == 200) {
						window.location.href = "/newest";
					}
				})
				.catch(error => {
					console.log(error);
				});

			this.postmessage = "";
		}
	}
}
</script>


<style lang="scss">
@import "../scss/global.scss";
</style>
