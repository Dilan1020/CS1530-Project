<template>
	<div class="home">
		<h2>This is the home page</h2>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
		<post></post>
	</div>
</template>

<script>
import Post from '@/components/Post.vue'
export default {
	name: 'home',
		components: {
			Post
	}
}
</script>

<style lang="scss">
@import "../scss/global.scss";
</style>
