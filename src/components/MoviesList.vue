<template>
	<ul>
		<li v-for="(movie, index) in movies" :key="index">
			<Movie :movie="movie" />
		</li>
	</ul>
</template>

<script>

import Movie from './Movie.vue';

export default { 
	name: 'MoviesList',
	created: function() {
		this.fetchData();
	},
	methods: {
		fetchData: async function() {
			try {
				const res = await fetch(
					'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=a801043160624e00167982916b8047c5'
				);
				const movies = await res.json();
				this.movies = movies.results;
			} catch(e) {
				console.log(e);
			}
		}
	},
	components: {
		Movie
	},
	data() {
		return {
			movies: [] 
		};
	}
};
</script>

<style lang="css" scoped>
	ul {
		display: grid;
		list-style: none;
		padding: 1rem;
		margin: 0;
		grid-row-gap: 1rem;
		grid-template-columns: repeat(6, 1fr);
	}
	li {
		padding: 1rem;
	}
</style>
