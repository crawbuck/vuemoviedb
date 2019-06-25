<template>
	<router-link :to="moviePath">
		<img :src="posterImage" :alt="movie.title" />
	</router-link>
</template>

<script>
const posterPath = "http://image.tmdb.org/t/p/original";
export default {
  props: ['movie'],
  computed: {
  	posterImage: function() {
  		return `${posterPath}/${this.movie.poster_path}`;
  	},
  	moviePath: function() {
  		return `/movie/${this.movie.id}`;
  	}
  }
};
</script>

<style lang="css" scoped>
	img {
		box-shadow: 0 0 35px black;
		width: 100%;
	}
</style>
