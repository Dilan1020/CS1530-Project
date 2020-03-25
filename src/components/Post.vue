<template>
	<div class="post">
		<div class="message">
			<h4>post</h4>
		</div>

		<div class="vote">
			<font-awesome-icon icon="angle-up" />
			<div class="count">0</div><!--  to be dynamically injected/calculated -->
			<font-awesome-icon icon="angle-down" />
		</div>
	</div>
</template>

<script>
export default {
	name: 'Post',
		props: {
			msg: String
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
