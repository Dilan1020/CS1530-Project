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
		votecount: Number
	},
	data: function() {
		return {
			
		}
	}
}
</script>

<script>
export default {
	methods: {
		voteUp: function(event) {
			console.log("up vote")
		},
		voteDown: function(event) {
			console.log("down vote")
		}
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
