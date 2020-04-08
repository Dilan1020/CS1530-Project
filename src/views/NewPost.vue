<template>
	<div class="newpostcontainer">
		<textarea v-model="postmessage" class="posttext"></textarea>
		<button v-on:click="clickHandler" class="postbutton">POST</button>
		<p>{{ postmessage }}</p>
	</div>
</template>

<script>
export default {
	data() {
		return {
			postmessage: ""
		}
	}
}
</script>

<script>
export default {
	methods: {
		clickHandler: function(event) {
			console.log("click registered")
		}
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
