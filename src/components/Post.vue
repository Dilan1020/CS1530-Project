<template>
	<div class="post">
		<div class="message">
			<h4>{{ msg }}</h4>
		</div>

		<div class="vote">
				<font-awesome-icon icon="angle-up" />
				<div class="votecount"> {{ votecount }} </div>
				<font-awesome-icon icon="angle-down" />
		</div>
	</div>
</template>

<script>
export default {
	name: 'Post',
	props: {
		msg: String,
		votecount: Number
	},
	data: function() {
		return {

		}
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
