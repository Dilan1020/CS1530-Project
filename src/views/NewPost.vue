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
			baseurl: 'http://localhost:8080/postNewPost?',
			latitude: null,
			longitude: null
		}
	},
	mounted() {
		if (!navigator.geolocation) {
			// status.textContent = 'Geolocation is not supported by your browser';
			this.cannotGetLocation();
		} else {
			navigator.geolocation.getCurrentPosition(this.getLocation, this.cannotGetLocation);
		}
	},
	methods: {
		cannotGetLocation() {
			alert("can't get location");
		},
		getLocation(position) {
			this.latitude = position.coords.latitude;
			this.longitude = position.coords.longitude;
			console.log("my location is: " + this.latitude + ", " + this.longitude);
		},
		clickHandler: function(event) {
			console.log(this.postmessage);

			let url = this.baseurl + 'userLatitude=' + this.latitude
									+ '&userLongitude=' + this.longitude
									+ '&postText=' + this.postmessage;
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
