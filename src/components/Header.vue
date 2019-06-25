<template>
	<header>
		<router-link to="/">
			<h1>{{ title }}</h1>
		</router-link>
	</header>
</template>

<script>
	export default{
		name: `Header`,
		props: {
			title: String
		},
		data() {
			return {
				show: false,
				name: `Michael`
			}
		},
		computed: {
			newTitle: function() {
				if (this.title === `hello`) {
					return this.title;
				}
				return this.name;
			}
		}
	};
</script>

<style scoped>
	header {
		background-color: #111;
		color: white;
		padding: 20px;
	}
	h1 {
		margin: 0;
	}
	header a {
		color: white;
		text-decoration: none;
	}
</style>