<template>
	<div class="newpostcontainer">
		<textarea v-model="postmessage" class="posttext"></textarea>
		<button class="postbutton"><Strong>POST</Strong></button>
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

<style lang="scss">
@import "../scss/global.scss";
</style>
