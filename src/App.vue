<template>
	<div id="app">
		<div id="nav">
			<router-link to="/">Newest</router-link> |
			<router-link to="/hottest">Hottest</router-link>
			<div class="newpostbutton">
				<router-link to="/newpost"><font-awesome-icon icon="plus-square" size="2x" /></router-link>
			</div>
		</div>
	<router-view/>
	</div>
</template>
