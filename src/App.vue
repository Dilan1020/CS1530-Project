<template>
	<div id="app">
		<div id="nav">
			<router-link v-bind:class="{'color-route': $route.path == '/'}" to="/">Newest</router-link> |
			<router-link v-bind:class="{'color-route': $route.path == '/hottest'}" to="/hottest">Hottest</router-link> |
			<router-link v-bind:class="{'color-route': $route.path == '/nearest'}" to="/nearest">Nearest</router-link>
			<div class="newpostbutton">
				<router-link to="/newpost"><font-awesome-icon icon="plus-square" size="2x" /></router-link>
			</div>
		</div>
	<router-view/>
	</div>
</template>
