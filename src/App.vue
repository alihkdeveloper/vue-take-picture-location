<template>
	<HelloWorld />

	<h3 id="location"></h3>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
	name: "App",
	data() {
		return {
			longitude: null,
			latitude: null,
		};
	},
	components: {
		HelloWorld,
	},
	created() {
		const success = (position) => {
			const getLatitude = position.coords.latitude;
			const getLongitude = position.coords.longitude;
			document.getElementById(
				"location"
			).innerText = `Latitude: ${getLatitude} - Longitude: ${getLongitude}`;
			// Do something with the position
		};

		const error = (err) => {
			console.log(err);
		};

		// This will open permission popup
		navigator.geolocation.getCurrentPosition(success, error);
	},
};
</script>
