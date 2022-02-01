<template>
	<div id="app" class="ui container">
		<h1>&lt;Vuetable-2&gt;</h1>
		<vuetable
			api-url="https://superauto.pet/api.json"
			:fields="fields"
			:transform="transformData"
			data-path=""
			pagination-path=""
			:css="css.table"
		></vuetable>
	</div>
</template>

<script>
import Vuetable from 'vuetable-2';
import VuetableCssBootstrap from './VuetableCssBootstrap4.js';

export default {
	name: 'App',
	components: {
		Vuetable,
	},
	data() {
		return {
			fields: ['name', 'tier', 'baseAttack', 'baseHealth', 'level1Ability'],
			css: VuetableCssBootstrap,
		};
	},
	methods: {
		transformData(data) {
			var result = [];
			var pets = data['pets'];

			for (var pet in pets) {
				if (Object.prototype.hasOwnProperty.call(pets, pet)) {
					result.push({
						name: pets[pet]['name'],
						tier: pets[pet]['tier'],
						baseAttack: pets[pet]['baseAttack'],
						baseHealth: pets[pet]['baseHealth'],
						level1Ability: pets[pet]['level1Ability'],
					});
				}
			}
			return result;
		},
	},
};
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	margin-top: 20px;
}
.vuetable tbody td {
	overflow: hidden;
	text-overflow: ellipsis;
}
</style>
